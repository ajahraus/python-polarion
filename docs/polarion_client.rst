Polarion client
===============

The polarion connects to the WSDL services of the Polarion service. These are listed at <polarion_url>/ws/services.
It is important that the url it the url where you normally login. So it should include /polarion in most cases.

Initialization
--------------
The class can be instantiated like this:

.. code:: python

    pol = polarion.Polarion('http://example.com/polarion', 'user', 'password')
    print(pol) # Polarion client for http://example.com/polarion/ws/services with user <user>

Token
-----
If you are using a token to autenticates:

.. code:: python

    pol = polarion.Polarion('http://example.com/polarion', 'user', password=None, token='token')
    print(pol) # Polarion client for http://example.com/polarion/ws/services with user <user>

Proxy
-----
You can specify a proxy by providing an domain or ip with a port number.

.. code:: python

    pol = polarion.Polarion('http://example.com/polarion', 'user', 'password', proxy='ip:port')


Self signed certificates
------------------------

If your polarion instance has a self signed certificate or an expired certificate, a https connections will be rejected.
You can skip certificate verification by passed an additional argument.

.. code:: python

    pol = polarion.Polarion('http://example.com/polarion', 'user', 'password', skip_cert_verification=False)

SVN repository location
-----------------------

The SVN repository access can be different from the standard (http://example.com/repo).
If this is the case, pass the new location using svn_repo_url. This is used while download attachment form test runs or test records.

.. code:: python

    pol = polarion.Polarion('http://example.com/polarion', 'user', 'password', svn_repo_url='http://example.com/repo_location')


Services
--------
Typically you would not use any service directly, but it is an option. Using it this way would ensure the session is still valid. 

.. warning::
    The refreshing of the session is still an open issue and not yet implemented. Using this module for prolonged time will likely lead to an ended session.

.. code:: python

    pol = polarion.Polarion('http://example.com/polarion', 'user', 'password')
    s = pol.getService('Tracker')
    print(s) # <zeep.proxy.ServiceProxy object at 0x0000025C01BF3A48>


Polarion class
--------------

.. autoclass:: polarion.polarion.Polarion
    :members:
