ETA
===

This is a python package that will create progress bars for command-line programs.

Example usage:

    from eta import ETA
    eta = ETA(ticks)
    for foo in bar:
        eta.print_status()
    eta.done()

Or, file based usage (calls tell() to get progress)

    fobj = open(fname)
    eta = ETA(os.stat(fname).st_size, fileobj=fobj)

    for line in fobj:
        eta.print_status(extra="extra message")
        ...
    eta.done()

The output is something similar to:

    20.0% - 0:04 [====>               ] ETA: 0:17 (Optional messages go here)

The default is to only display the progress bar *if* stderr is connected to a
terminal (sys.stderr.isatty() is True). If you want to always enable the
progress bar, you need to set the evironmental variable 'SHOW_ETA'.

To hide the progress bar (for use in other batch scripts), you can hide the
progress bar by setting the environmental variable 'HIDE_ETA'.

The default is to update the progress bar every 0.2 sec, unless we aren't
attached to a tty (and SHOW_ETA is set). In this case, the progress updates
every 10 seconds. 

