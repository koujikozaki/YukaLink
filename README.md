# YukaLink

### 大阪府に縁のある「人物」「作品」「会社」の数を調べる
```
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT ?type ?typeLabel (count(?s) AS ?c)
FROM <http://lod.hozo.jp/YukaLink/DBpediaJP/>
FROM <http://lod.hozo.jp/YukaLink/Wikidata/>
WHERE {
?pref rdfs:label "大阪府"@ja.
VALUES ?type {dbo:Person dbo:Work dbo:Company}
  {?s ?p1 ?pref}
UNION{?pref ?p2 ?s.}
  ?s a ?type .
  ?type rdfs:label ?typeLabel. 
}GROUP BY ?type ?typeLabel
ORDER BY DESC(?c)
```
[クエリの実行](https://api.triplydb.com/s/gSDecFlNR)
