Python Module for Pingdom REST API
==================================

Description
-----------

Simple Python wrapper for the `Pingdom REST API`_.

This module does not support the soon-to-be obsolete `Pingdom SOAP API`_.
See `python-pingdom`_ for the SOAP interface.

Dependencies
------------
None beyond the Python standard library.

Usage
-----

Instantiate::

    import pingdom
    p = pingdom.Pingdom(username=YourUserName, password=YourPassword, appkey=YourAppKey)

Call an arbitrary method as described in the API docs::

    p.method(url='method/url/', method="GET/POST/PUT/etc", parameters={'name':'value', })

Example methods::

    # List checks
    p.method('checks')
    
    # Modifiy a check, in this case, pause it
    p.method('checks/CHECK_ID_NUM/', method='PUT', parameters={'paused': True})
    
Some shortcut methods that were useful to me::

    # Get checks by name instead of number
    p.check_by_name('my check name')
    
    # Pause and unpause a check by name
    p.pause_check('my check name')
    p.unpause_check('my check name')
    
    # Average Response Time
    p.avg_response(CHEKC_ID_NUM)

    # Average Response Time for the last 15 minutes
    p.avg_response(CHEKC_ID_NUM, minutes_back=15)

    # Average Response Time for the last 15 minutes in the US
    p.avg_response(CHEKC_ID_NUM, minutes_back=15, country='US')
    
    

.. _`Pingdom REST API`: http://www.pingdom.com/services/api-documentation-rest/
.. _`Pingdom SOAP API`: http://www.pingdom.com/services/api-documentation/
.. _`python-pingdom`: https://github.com/danudey/python-pingdom
