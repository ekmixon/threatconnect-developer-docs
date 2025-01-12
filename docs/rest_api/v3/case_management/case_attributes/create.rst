Create Case Attributes
----------------------

The most basic format for adding a Case Attribute to a Case is:

.. code::

    POST /v3/caseAttributes/
    {
      "caseId": 1,
      "type": "Case Attribute Type",
      "value": "Case Attribute Value"
    }

Additional fields can be included when adding a Case Attribute to a Case, Refer to the following table for a list of available fields for the ``caseAttributes`` object:

+-----------+---------------------------------------------------+----------+----------+------------------------+
| Field     | Description                                       | Required | Type     | Example Value(s)       |
+===========+===================================================+==========+==========+========================+
| caseId    | The ID of the Case associated to the Attribute    | TRUE     | Integer  | 1, 2, 3                |
+-----------+---------------------------------------------------+----------+----------+------------------------+
| source    | The Attribute's source                            | FALSE    | String   | "Hybrid analysis"      |
+-----------+---------------------------------------------------+----------+----------+------------------------+
| type      | The contents of the Note itself                   | TRUE     | String   | "Detection percentage" |
+-----------+---------------------------------------------------+----------+----------+------------------------+
| value     | The ID of the Event on which to apply the Note    | TRUE     | String   | "50"                   |
+-----------+---------------------------------------------------+----------+----------+------------------------+

.. note:: Attribute Types for Cases must first be created in the System or Organization in which a Case resides before they can be added to the Case. See `Creating Custom Attribute Types <https://training.threatconnect.com/learn/article/creating-custom-attributes-kb-article>`__ for more information.

.. note:: Trying to add an Attribute to a Case when the Case Attribute Type's **Max Allowed** limit has been reached will result in an error.
  
For example, the following query will add a Case Attribute to the Case with ID 1.

.. code::

    POST /v3/caseAttributes/
    {
      "caseId": 1,
      "type": "Detection Percentage",
      "value": "50",
      "source": "Hybrid analysis"
    }

JSON Response:

.. code:: json

    {
      "data": {
          "id": 13,
          "type": "Detection Percentage",
          "value": "50",
          "source": "Hybrid analysis"
      },
      "message": "Created",
      "status": "Success"
    }
