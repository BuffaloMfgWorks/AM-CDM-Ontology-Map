# AM-CDM-Ontology-Map
This repository contains OWL files that contain a mapping of the Additive Manufacturing Common Data Model (AM-CDM) to Basic Formal Ontology (BFO) via The Common Core Ontologies' (CCO) Information Entity Ontology. 

1. The best way to view the mapping is through the Merged file. This places every class in their appropriate subclass relation regardless of the import structure of the AM-CDM modules. 

2. Classes in the AM-CDM such as 'person' and 'system' in the AM-CDM function as buckets that retain all information pertinent to the class. These classes are placed in a subclass relation to Information Content Entity classes in the IEO based on the nature of the primary ID of the class. For example, AM-CDM: Person is a subclass of CCO:Designative ICE because the primary ID will either be an Email, a person ID, or a Name. Each of these entities is classified as a Designative ICE in CCO. 

3. The class restrictions are best understood as what a user should place in the bucket when sharing information and what one should expect to recieve in a bucket that has been shared with them. For example, when sharing information on a person, the organization should include their name, email address, ID, phone numnber, organization affiliation, and credentials.

4. Data properties from AM-CDM such as 'address line 1' and 'purchase order number' have been converted to document fields (address line 1 document field; purchase order number document field). A python script will be created and stored in this repo that ensures that any string or integer connected to an entity by the data property will nbe connected to the corresponding Document field via CCO data properties like has_text_value and has_integer_value. 

5. Given (3) and (4), the intended way to understand the the mapped filse is that the ICE is carried by the aggregate of document fields in the restriction. For example, the ICE equivalent of person is carried by the document fields with their name, email address, ID, phone numnber, organization affiliation, and credentials. If one document field is empty, then the ICE is incomplete. 
