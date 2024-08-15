:original_name: apig-en-api-180328006.html

.. _apig-en-api-180328006:

Signing a Request
=================

#. .. _apig-en-api-180328006__li17137133433914:

   Introduce the API Gateway signing SDK in the project.

   a. Download the API Gateway signing tool from the following link:

      https://apig-demo.obs.eu-de.otc.t-systems.com/java/java-sdk-core.zip

   b. Decompress the downloaded package to obtain a **.jar** file.

   c. Add the decompressed **.jar** file to a project, for example, Eclipse, as a dependency package. See the following figure.

      |image1|

#. Sign the request.

   The signing method is integrated into the **.jar** file added in :ref:`1 <apig-en-api-180328006__li17137133433914>`. Before sending the request, sign the requested content. The signature obtained is included in the HTTP header of the request.

   For details, see :ref:`Sample Code <apig-en-api-180328008>`.

   .. important::

      The JDK version cannot be earlier than 1.8.

.. |image1| image:: /_static/images/en-us_image_0132557229.png
