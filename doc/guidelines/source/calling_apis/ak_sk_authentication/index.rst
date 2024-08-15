:original_name: apig-en-api-180328004.html

.. _apig-en-api-180328004:

AK/SK Authentication
====================

When you use API Gateway to send requests to underlying services, the requests must be signed using the AK and SK.

.. note::

   AK is a unique identifier that is associated with a secret access key; the access key ID and secret access key are used together to sign requests cryptographically.

   SK is a key that is used in conjunction with an access key ID to cryptographically sign requests. Signing a request identifies the sender and prevents the request from being altered.

The AK/SK authentication process is as follows:

#. .. _apig-en-api-180328004__li889518531076:

   A standard request is created.

#. A to-be-signed string is created using the request and other related information.

#. .. _apig-en-api-180328004__li198402221915:

   A signature is calculated using the AK/SK and to-be-signed string.

#. The generated signature is added as a header or a query parameter in the HTTP request.

#. After receiving the request, API Gateway performs :ref:`1 <apig-en-api-180328004__li889518531076>` to :ref:`3 <apig-en-api-180328004__li198402221915>` to calculate a signature.

#. The new signature is compared with the signature generated in :ref:`3 <apig-en-api-180328004__li198402221915>`. If they are consistent, the request is processed; otherwise, the request is rejected.

:ref:`Figure 1 <apig-en-api-180328004__fig104904517537>` shows the process of calling APIs through AK/SK authentication.

.. _apig-en-api-180328004__fig104904517537:

.. figure:: /_static/images/en-us_image_0161965716.png
   :alt: **Figure 1** API calling process flow

   **Figure 1** API calling process flow

.. note::

   -  If a failure occurs in any step, the failure will be returned to the client application.
   -  The cached token is valid for 15 minutes by default.

-  :ref:`Generating an AK and SK <apig-en-api-180328005>`
-  :ref:`Signing a Request <apig-en-api-180328006>`
-  :ref:`Sample Code <apig-en-api-180328008>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   generating_an_ak_and_sk
   signing_a_request
   sample_code
