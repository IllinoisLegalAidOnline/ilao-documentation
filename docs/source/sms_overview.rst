==================
SMS Overview
==================

We deliver many things over SMS.

Online intake and triage
==========================

ILAO has a short code that processes inbound requests for users to apply for free legal help.


See :ref:`otis-sms-label`

REST-based messaging
=====================

We will also use SMS for a few other use cases that run over API. These are sent over REST from the website or Zapier-based transactions to specific flows. Currently, we use REST for reminders, the SMS feedback survey, and Know your rights (KYR) follow up surveys.

+-----------------------+--------------------------------+------------------------+
| REST App              | Flow                           | Status                 |
+=======================+================================+========================+
| sms                   | SMS follow up survey           | Built as flow          |
+-----------------------+--------------------------------+------------------------+
| kyr follow up surveys | KYR surveys                    | Built as flow          |
+-----------------------+--------------------------------+------------------------+
| Otis confirmations    | N/A                            | Built in code          |
+-----------------------+--------------------------------+------------------------+
| OTIS reminders        | Not yet built                  | In backlog             |
+-----------------------+--------------------------------+------------------------+
| Next steps from       | Not yet built                  | Not defined            |
| content               |                                |                        |
+-----------------------+--------------------------------+------------------------+
| Feedback surveys      | Not yet built                  | Not defined            |
+-----------------------+--------------------------------+------------------------+


