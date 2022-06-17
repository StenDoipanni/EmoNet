# EmoNet
EmoNet is the repository for knowledge graphs including semantic triggers of Emotions that operationalize different Emotion Theories.


## Building the Resource

Here you find listed some of the queries performed to the [Framester]() endpoint to retrieve emotion semantic triggers.

Query to retrieve all the verbs from VerbNet and PropBank using some lexical unit as variable. 

```
PREFIX fschema: <https://w3id.org/framester/schema/>
SELECT DISTINCT ?vb
WHERE{

"some_variable" <https://w3id.org/framester/wn/wn30/schema/containsWordSense> ?o .
?o <https://w3id.org/framester/wn/wn30/schema/senseKey> ?o2 .
?vb <https://w3id.org/framester/vn/schema/mapsToWordSenseKey> ?o2 .
}


```


Query to retrieve all the frames and WordNet synsets from some lexical unit used as variable. 

```
PREFIX fschema: <https://w3id.org/framester/schema/>
SELECT DISTINCT ?frame ?syn
WHERE{
?frame rdf:type fschema:ConceptualFrame , owl:Class ;
  rdfs:subClassOf fschema:FrameOccurrence ;
  owl:sameAs ?fnframe .
?fnframe skos:closeMatch ?syn ; a fn15schema:Frame .
FILTER(regex(?syn, "insert_variable", "i"))
}
            
```
