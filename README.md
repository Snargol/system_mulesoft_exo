# system_mulesoft_exo
 
Contexte
Mettre en place 3 applications mulesoft qui vont communiquer entre elles et les déployer sur CloudHub.
Application 1 : va exposer des données brut venant d’une source extérieure (dans notre cas les données seront hard coded dans l’application.
Application 2: Récupérer les informations de l’application 2, effectuer du filtrage et des calculs et exposer les données au format xml .
Application 3 : TODO



Application 1

Créer des spec api permettant de récupérer les données via un endpoint “/contracts” et une méthode “GET”
Créer un flow “data1” qui va stocker les données dans un transformMassage
Les données en question sont :

`
[
  {
    "Contract_ID": "10",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "301207461",
    "Salesman_ID": "800023000126",
    "SalesUnit_ID": "21M233COPL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-04-2018",
    "CUTOFF_AMOUNT": 64.4
  },
  {
    "Contract_ID": "11",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "301207461",
    "Salesman_ID": "80020000126",
    "SalesUnit_ID": "21M123COPL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-05-2018",
    "CUTOFF_AMOUNT": 1932.13
  },
  {
    "Contract_ID": "33",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "30307461",
    "Salesman_ID": "800230000126",
    "SalesUnit_ID": "21M12COPL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-06-2018",
    "CUTOFF_AMOUNT": 1932.13
  },
  {
    "Contract_ID": "-2",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "300327461",
    "Salesman_ID": "800022000126",
    "SalesUnit_ID": "21MC12OPL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-07-2018",
    "CUTOFF_AMOUNT": 1932.13
  },
  {
    "Contract_ID": "",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "30027461",
    "Salesman_ID": "80001000126",
    "SalesUnit_ID": "21MC21OPL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-08-2018",
    "CUTOFF_AMOUNT": 1932.13
  },
  {
    "Contract_ID": "2",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "300227461",
    "Salesman_ID": "800120000126",
    "SalesUnit_ID": "21MCOPL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-09-2018",
    "CUTOFF_AMOUNT": 1932.13
  },
  {
    "Contract_ID": "118",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "3007461",
    "Salesman_ID": "80000200126",
    "SalesUnit_ID": "21MC12PL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-10-2018",
    "CUTOFF_AMOUNT": 1932.13
  },
  {
    "Contract_ID": "119",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "30071461",
    "Salesman_ID": "800021000126",
    "SalesUnit_ID": "21M21COPL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-11-2018",
    "CUTOFF_AMOUNT": 1932.13
  },
  {
    "Contract_ID": "121",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "3007461",
    "Salesman_ID": "800120000126",
    "SalesUnit_ID": "21MC2OPL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-12-2018",
    "CUTOFF_AMOUNT": 1932.13
  },
  {
    "Contract_ID": "122",
    "Creation_Date": "21-02-2019",
    "Start_Date": "30-04-2018",
    "End_Date": "30-04-2019",
    "Customer_ID": "3007461",
    "Salesman_ID": "800012000126",
    "SalesUnit_ID": "21MCO2PL-EVFR-01",
    "Amount": "23250.000000",
    "Contract_Name": "",
    "Currency_Code": "EUR",
    "Renew": "",
    "Customer_Name": "",
    "Salesman_Name": "",
    "SalesUnit_Name": "",
    "Number_Of_Months": 12.03,
    "Opportunity_ID": null,
    "CUTOFF_MONTH": "01-01-2019",
    "CUTOFF_AMOUNT": 1932.13
  }
]
`

Créer un flow “data_expose” qui va faire appel au flow “data1” et exposer les données
Ajouter un logger à la fin du flow “data_expose” pour savoir quand est effectué chaque appel (un simple message text suffit)
Appeler le flow “data_expose” depuis le flow généré par les specs.
