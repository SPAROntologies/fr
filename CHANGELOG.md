# Changelog

* **v2.0.1**:
Added new documentation files to the repository (e.g., the `CITATION.cff` file) and refactored some components.
* **v2.0.0**: 
Added new documentation, including annotation properties (e.g., `bibo:doi`, `schema:codeRepository`, etc.), term properties (e.g., `vann:example`, `vs:term_status`, etc.), exemplary competency questions with their respective SPARQL queries, and a Grafoo diagram.
Added the additional classes and properties from external ontologies.
Replaced `fr:ratingValue` with `bido:hasRatingValue`, given they were identical in their implementation and the latter already existed.
Replaced `skos:inScheme` with `bido:isDefinedIn`, given it is its subproperty that is applicable to categorical bibliometric data, such as in this case.
