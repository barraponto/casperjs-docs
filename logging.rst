=======
Logging
=======

CasperJS allows logging using its ```log()`` <api.html#casper.log>`_
method and these standard event levels:

-  ``debug``
-  ``info``
-  ``warning``
-  ``error``

Sample use:

::

    var casper = require('casper').create();
    casper.log('plop', 'debug');
    casper.log('plip', 'warning');

Now, there are two things to distinguish: log *storage* and log
*display*; by default CasperJS won't print the logs to the standard
output. In order to do so, you must enable the ``verbose`` Casper
option:

::

    var casper = require('casper').create({
        verbose: true
    });

Also, by default Casper is configured to filter logging which is under
the ``error`` level; you can override this setting by configuring the
``logLevel`` option:

::

    var casper = require('casper').create({
        verbose: true,
        logLevel: 'debug'
    });

You can also dump a JSON log of your Casper suite just by rendering the
contents of the ``Casper.logs`` property:

::

    var casper = require('casper').create({
    // ...
    casper.run(function() {
        this.echo(JSON.stringify(this.logs, null, 4)).exit();
    });

Last, if you print log messages to the standard output using the
``verbose`` option, you'll get some fancy colors:

::

    var casper = require('casper').create({
        verbose: true,
        logLevel: 'debug'
    })
    casper.log('this is a debug message', 'debug');
    casper.log('and an informative one', 'info');
    casper.log('and a warning', 'warning');
    casper.log('and an error', 'error');
    casper.exit();

This will give the following output:

.. figure:: images/logoutput.png
   :align: center
   :alt: image

   image

