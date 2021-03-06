Realtime DTrace Analysis
========================

A collection of scripts used for realtime DTrace visualizations and analysis

Stream gnuplot
--------------

`stream-gnuplot.sh` is a script that reads from stdin to generate live gnuplot
graphs.  It takes input in the form of:

    <epoch> <y-axis>\n

The DTrace scripts provided will output in this format, so they can be piped into
`stream-gnuplot.sh`.

Examples
--------

### Syscall Latency/Count Visualization

Visualize syscall latency or counts using gnuplot.  An example of this can be seen here
http://www.youtube.com/watch?v=PnvszdcUgJc

    $ sudo ./syscall-latency.d 'read*' | ./stream-gnulpot.sh

      20 ++------+-------+------+-------+-------+-------+------+-------+------++
         +       +       +      +       + "-" using ($1):($2/1000/1000)+****** +
      18 ++                                                    *              ++
      16 ++                                                   * *             ++
         |                                                    * *              |
      14 ++                                                  *   *            ++
         |                                                   *   *             |
      12 ++                                                 *     *           ++
      10 ++                                                 *      *          ++
         |                              **                 *       *           |
       8 ++                           **  **               *        *         ++
         |                           *      *             *          *         |
       6 ++                         *        *            *          *        ++
         |                        **          **         *            *        |
       4 ++                      *                       *            *       ++
       2 ************************               *********              ********+
         +       +       +      +       +       +       +      +       +       *
       0 ++------+-------+------+-------+-------+-------+------+-------+------++
       11:02   11:03   11:04  11:05   11:06   11:07   11:08  11:09   11:10   11:11
                                     Time (Seconds)


License
-------

BSD 3 Clause.  See LICENSE for details.
