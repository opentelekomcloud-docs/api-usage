:original_name: apig-en-api-180328003.html

.. _apig-en-api-180328003:

Token Authentication
====================

Application Scenarios
---------------------

If API requests are authenticated using tokens, the request header must contain **X-Auth-Token** (token information).

This section describes how to call an API for token authentication.

Procedure
---------

#. Send **POST https://**\ *IAM endpoint*\ **/v3/auth/tokens** to obtain the IAM endpoint and the region name in the message body.

   See `Regions and Endpoints <https://docs.otc.t-systems.com/regions-and-endpoints/index.html>`__.

   A cloud service can be deployed globally or at the project level.

   -  A project-level service requires a project-level token. When you call the API, set **auth.scope** in the request body to **project**. The following services are at the project level: AOM, APIG, AS, BMS, CBR, CCE, Cloud Eye, CSBS, CSS, CTS, DataArts Studio, DC, DCS, DDS, Dedicated WAF, DeH, DIS, DLI, DMS, DNS, DRS, DWS, ECS, EIP, ELB, EVS, GaussDB (for MySQL), GaussDB NoSQL, IMS, KMS, LTS, ModelArts, MRS, NAT, PLAS, RDS, RTS, SDRS, SFS, SMN, SWR, VBS, VPC, VPCEP, VPN, and WAF.
   -  A global service requires a global token. When you call the API, set **auth.scope** in the request body to **domain**. The following services are global ones: Anti-DDoS, IAM, OBS, TMS, and TMS.

   The following shows an example of a project-level service request:

   .. note::

      Replace the texts in italic with actual ones. For details, see *Identity and Access Management API Reference*.

      Log in to the management console, click your username in the upper right corner, and choose **My Credential** from the drop-down list. On the **My Credentials** page, obtain your username, domain name, and project ID.

   .. code-block::

      {
        "auth": {
          "identity": {
            "methods": [
              "password"
            ],
            "password": {
              "user": {
                "name": "username", // IAM username
                "password": "password",  // IAM user password
                "domain": {
                  "name": "domainname" // Name of the domain to which the IAM user belongs
                }
              }
            }
          },
          "scope": {
            "project": {
              "id": "0215ef11e49d4743be23dd97a1561e91" // Project ID
            }
          }
        }
      }

   The following shows an example of a global service request:

   .. code-block::

      {
          "auth": {
              "identity": {
                  "methods": [
                      "password"
                  ],
                  "password": {
                      "user": {
                          "name": "username",   // IAM username
                          "password": "password",  // IAM user password
                          "domain": {
                              "name": "domainname"  // Name of the domain to which the IAM user belongs
                          }
                      }
                  }
              },
              "scope": {
                  "domain": {
                      "name": "domainname"    // Name of the domain to which the IAM user belongs
                  }
              }
          }
      }

#. .. _apig-en-api-180328003__li2615608112249:

   Obtain the token. For details, see section "Obtaining the User Token" in the *Identity and Access Management API Reference*. If the request is successful, the value of the X-Subject-Token header in the response is the token.

   The following figures illustrate how to use Postman to manually obtain a token.


   .. figure:: /_static/images/en-us_image_0139098594.png
      :alt: **Figure 1** Example request

      **Figure 1** Example request


   .. figure:: /_static/images/en-us_image_0139099203.png
      :alt: **Figure 2** Obtain **X-Subject-Token** from the header of the response message.

      **Figure 2** Obtain **X-Subject-Token** from the header of the response message.

#. Call a service API, add the **X-Auth-Token** header with the token obtained in :ref:`2 <apig-en-api-180328003__li2615608112249>`.
