```mermaid
%%{
    init: {
        'theme': 'base',
        'themeVariables': {
            'primaryColor': '#000000',
            'primaryTextColor': '#000000',
            'primaryBorderColor': '#000000',
            'lineColor': '#000000',
        }
    }
}%%

graph TD;
    websites@{ shape: processes, label: "Websites"}-- scrape data -->processor[Clean and validate data]
    files@{ shape: docs, label: "Raw .csv, \n.xlsx, .pdf files" }-- extract data -->processor
    source_x@{ shape: processes, label: "Other data sources"}-- extract data -->processor
    processor-->calculator[Run calculations and build relations]
    tester[Test suite]-.-processor
    tester-.-calculator
    calculator-->database[(Database)]-->app{User-facing application}


   subgraph legend [Color Legend]
       sourceLegend[Source Data]
       programLegend[Python Program]
       useLegend[Data Storage]
   end

   classDef sourceData fill:#6495ED,stroke:#000000;
   class sourceLegend,websites,files,source_x sourceData;

   classDef program fill:#6EAA32,stroke:#000000;
   class programLegend,processor,calculator,tester program;

   classDef use fill:#BF6C8A,stroke:#000000;
   class useLegend,database,app use;
```
