## Competency Questions

FR can be used for answering several questions related to research reviews characteristics. 
In the following subsections, some of them are introduced together with their respective SPARQL queries. 

The prefixes that are used in all the SPARQL queries provided below are defined as follows:

	PREFIX fr: <http://purl.org/spar/fr/>
	PREFIX c4o: <http://purl.org/spar/c4o/>
	PREFIX cito: <http://purl.org/spar/cito/>
	PREFIX dcterms: <http://purl.org/dc/terms/>
	PREFIX fabio: <http://purl.org/spar/fabio/>
	PREFIX frbr: <http://purl.org/vocab/frbr/core#>

### CQ1

Which document is reviewed by a specific review version, and who is its creator?

	SELECT ?reviewVersion ?paper ?creator
	WHERE {
		?reviewVersion a fr:ReviewVersion ;
			cito:reviews ?paper .
		OPTIONAL { ?reviewVersion frbr:creator ?creator . }
	}

### CQ2

What rating and reviewer confidence score are assigned to a review version?

	SELECT ?reviewVersion ?rating ?confidence
	WHERE {
		?reviewVersion a fr:ReviewVersion ;
			fr:hasRating ?rating .
		OPTIONAL { ?reviewVersion fr:hasReviewerConfidence ?confidence . }
	}

### CQ3

At which platform was a review version issued, and for which venue or event was it issued?

	SELECT ?reviewVersion ?platform ?venue
	WHERE {
		?reviewVersion a fr:ReviewVersion ;
			fr:issuedAt ?platform .
		OPTIONAL { ?reviewVersion fr:issuedFor ?venue . }
	}

### CQ4

Which agent or entity released a review version, and on what date was it issued?

	SELECT ?reviewVersion ?releasingEntity ?issueDate
	WHERE {
		?reviewVersion a fr:ReviewVersion ;
			fr:releasedBy ?releasingEntity .
		OPTIONAL { ?reviewVersion dcterms:issued ?issueDate . }
	}

### CQ5

What is the full review version of a review, including its textual content and license?

	SELECT ?review ?reviewVersion ?content ?license
	WHERE {
		?review a fabio:Review ;
			frbr:realization ?reviewVersion .
		?reviewVersion a fr:ReviewVersion .
		OPTIONAL { ?reviewVersion c4o:hasContent ?content . }
		OPTIONAL { ?reviewVersion dcterms:license ?license . }
	}