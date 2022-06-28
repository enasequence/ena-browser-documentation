=========
Rulespace
=========

Introduction
============

Explore your saved Rules with Rulespace. From here you can create a new rule or 
share and re-run your saved rules generated from the 
`ENA Advanced Search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_.  

Log into Rulespace
==================

What is Rulespace?
------------------

Rulespace can be used to save, share and re-run custom search queries generated from the 
`ENA Advanced Search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_. 

Log in to access and manage your set of saved rules.

Log in using an AAP Account
---------------------------

The Authentication, Authorisation and Profile service (AAP) provides a central log-in 
for multiple different services at EMBL-EBI (and can be used by other services and 
organisations as required).

You can register for an AAP account `here <https://aai.ebi.ac.uk/registerUser>`_.

Log in using a Life Science Account
-----------------------------------

Logging in with your Life Science account enables you to log in to Rulespace use your
home or organisation credentials (including the options to log in with your 
Google, Apple or ORCID accounts).

To log in with LIFE SCIENCE, you first need to register for a `LIFE SCIENCE ID <https://lifescience-ri.eu/ls-login/users/how-to-get-and-use-life-science-id.html>`_.

You can register with LIFE SCIENCE `here <https://signup.aai.lifescience-ri.eu/fed/registrar/?vo=lifescience>`_.

Create a Rule
=============

To create a rule, you need to create a custom search query using the 
`ENA Advanced Search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_ service. 
Follow the step by step guide on creating a custom search query and defining the fields 
you want returned from your search.

When you are happy with your search click *Search* then, on the results page you 
have the option to save the search to Rulespace:

.. image:: images/rulespace-save.png

Share a Rule
============

You can share your rules with others by providing them with one of four following options:

1. **The Search URL** - you can copy and share a direct URL to the results from your rule 
search. This URL links directly to the resulting metadata in the specified format (TSV or JSON) 
(not to the results page) so can be used to programmatically access the results of the search if 
you wish. 

2. **The Rule URL** - you can copy and share a direct URL to the JSON object of the rule 
itself. This can be used to programmatically access information about the search parameters of 
the rule as well as information on when it was most recently updated.

3. **The Rule ID** - you can copy and share your rule ID which can be used to repeat the search 
you have saved in the `ENA Advanced Search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_ 
service.

4. **The Rule Name** - all rules have to be saved under a *unique name* so you can also copy and 
share your Rule name which can then be used to repeat your saved search in the 
`ENA Advanced Search <https://www.ebi.ac.uk/ena/browser/advanced-search>`_ service.

*Please note: Whenever the results of a Rulespace search are accessed, the search is performed 
again, live each time, so if data within the archive has changed since the last search, the results 
can vary since the search was last run.*

Accessing Rulespace Programmatically
====================================

The features of the Rulespace service can also be accessed directly via the API at:

https://www.ebi.ac.uk/ena/rulespace/api/

For more information on the Rulespace API service, you can 
access the API documentation `here <https://www.ebi.ac.uk/ena/rulespace/api/doc>`_.
