# AM-CDM-Ontology-Map

This repository contains two folders:

1. **CDM to CCO Maps**: Contains OWL files that map the Additive Manufacturing Common Data Model (AM-CDM) to the Basic Formal Ontology (BFO) via The Common Core Ontologies' (CCO) Information Entity Ontology (IEO).

2. **To Ontology**: Contains OWL files that align the AM-CDM with the real-world entities that the information classes in the AM-CDM represent.

## CDM to CCO Guidelines

1. **Merged File View**:
   - The best way to view the mapping is through the **Merged** file. This file places every class in their appropriate subclass relation, regardless of the import structure of the AM-CDM modules.

2. **Class Mapping**:
   - Classes in the AM-CDM, such as `person` and `system`, function as buckets that retain all information pertinent to the class. These classes are placed in a subclass relation to Information Content Entity (ICE) classes in the IEO based on the nature of the primary ID of the class. 
   - For example, `AM-CDM: Person` is a subclass of `CCO:ICE` because the primary ID will either be an Email, a person ID, or a Name. Each of these entities is classified as a Designative ICE in CCO.

3. **Class Restrictions**:
   - The class restrictions are best understood as what a user should place in the bucket when sharing information and what one should expect to receive in a bucket that has been shared with them.
   - For example, when sharing information on a person, the organization should include their name, email address, ID, phone number, organization affiliation, and credentials.

4. **Data Properties Conversion**:
   - Data properties from AM-CDM, such as `address line 1` and `purchase order number`, have been converted to document fields (e.g., `address line 1 document field`, `purchase order number document field`). 
   - A Python script will be created and stored in this repository to ensure that any string or integer connected to an entity by the data property will be connected to the corresponding document field via CCO data properties like `has_text_value` and `has_integer_value`.

5. **Understanding Mapped Files**:
   - Given points (3) and (4), the intended way to understand the mapped files is that the ICE is carried by the aggregate of document fields in the restriction. 
   - For example, the ICE equivalent of a person is carried by the document fields with their name, email address, ID, phone number, organization affiliation, and credentials. If one document field is empty, then the ICE is incomplete.

## To Ontology Guidelines

1. **Aboutness Relations**:
   - The **To Ontology** imports the map files and states what each class in the CDM is about.
   - For example, the `CDM:person` class is about the `CCO:person` class, and the `CDM:organization` class is about the `CCO:organization` class.

2. **MERIOT Method**:
   - To maintain a manageable size, each file uses the MERIOT method to import only necessary classes and their parentage.
   - For example, **BuildToOntology** MERIOTs `act of manufacturing` from the Event Ontology. In order to connect `act of manufacturing` to `BFO:process`, `act`, `planned act`, and `act of artifact processing` are also MERIOTed.
