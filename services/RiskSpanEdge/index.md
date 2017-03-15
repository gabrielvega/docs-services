---

copyright:

  years:  2017

lastupdated: "2017-03-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# Getting started with RiskSpanEdge
{: #gettingstarted_RiskSpanEdge}

RS Edge is a data discovery and modeling tool which prrovides access to billions of rows of mortgage performance data.  Our proprietary search and retrieval technology and scalable back-end data center allows for fast querying and ad-hoc analysis on-demand. Analysis is combined with RiskSpan's proprietary projection models to enable forecasting of credit and prepayment performance.
{:shortdesc}


RS Edge provides a REST API to the data and analytic engine. To integrate your app with the service, complete these steps: 
1. Obtain auth ID from RiskSpan
2. Create a bucketing criteria appropriate to your analysis
3. Select the required stress scenario.

**REST API parameters**

* auth_key - your key for accessing the RS Edge API
* deal_name - name of the portfolio being analyzed (Please use the sample portfolio: ABANK)
* trade_date - analysis date (YYYYMMDD format, example 2015 
* bucket_key - RS Edge XML query format
* scenario specification

**Output**

Output from the API is generated in JSON format. The output consists of:
* user defined data clusters
* user defined loan performance aggregates
* model performance including defaults and loss given defaults

**Sample call**

```
curl -H "Accept:application/json" "http://uat.riskspan.com:18080/RSEdgeRest/EdgeRestService?deal_name=_ABANK&trade_date=20170306&auth_key=XXXXXXXX&bucket_file=%3CNewBucketingFile%3E%3CDataset%20Value=%22_ABANK%22%20/%3E%3CBucket%20Type=%22FactorDate%22%20Min=%2220150301%22%20Max=%2220150301%22%20Step=%221%22%20/%3E%3CBucket%20Type=%22property_type%22%20Value=%22Condo~MH~PUD~SF~Townhouse%22%20FilterFlag=%221%22%20/%3E%3CResultset%20Value=%22ScenarioSevereStress%22/%3E%3C/NewBucketingFile%3E"
```
{: codeblock}
  
**Sample output** 

```
{"CollateralResults":{"MainRequestId":29,"LoanBucketing":{"LoanBucket":[{"DefaultUPB":"","Age":49.5817701114,"TotalDefault24":5239660.846315403,"KEY":"property_type_Bucket:Condo;FactorDate_Bucket:20150301","CurrentLTV":70.211543808,"AccountingUPB":7.575858368699983E8,"UPB":7.812104422499987E8,"DefaultUPBHistory":158592.6,"TotalDefault18":4216080.821061679,"TotalLoss24":1141830.3249466524,"ClusterName":"property_type_Bucket:Condo;FactorDate_Bucket:20150301","FICO":749.1648220001,"ObservedMDR":0.0341730639,"FactorDate":20150301,"LoanCount":5976,"WAC":4.2137057386,"DTI":35.1076264353,"NetLossHistory":23788.89,"WAM":59002.5249677329,"TotalDefault12":2901339.8170057754,"LTV":73.1464876249,"TotalLoss12":635203.8887912369,"NetLoss":"","RSModelMDR":0.0341730639,"AvgOrigUPB":258539.2533785137,"AvgLoanSize":190771.7807692304,"TotalLoss18":920717.5750741911},{"DefaultUPB":"","Age":51.8543205055,"TotalDefault24":623319.1757366426,"KEY":"property_type_Bucket:MH;FactorDate_Bucket:20150301","CurrentLTV":70.4936404906,"AccountingUPB":7.401843491999997E7,"UPB":7.492019342999998E7,"DefaultUPBHistory":0,"TotalDefault18":501312.9897102259,"TotalLoss24":156307.3429592932,"ClusterName":"property_type_Bucket:MH;FactorDate_Bucket:20150301","FICO":747.2270057512,"ObservedMDR":0.0414980368,"FactorDate":20150301,"LoanCount":903,"WAC":5.2590835966,"DTI":32.7015737166,"NetLossHistory":0,"WAM":308.1426454657,"TotalDefault12":344770.4825940511,"LTV":73.7041292784,"TotalLoss12":86748.1884397957,"NetLoss":"","RSModelMDR":0.0414980368,"AvgOrigUPB":99946.8438538206,"AvgLoanSize":90483.3253985507,"TotalLoss18":125907.7080114835},{"DefaultUPB":"","Age":40.3695906348,"TotalDefault24":1.049387823253114E7,"KEY":"property_type_Bucket:PUD;FactorDate_Bucket:20150301","CurrentLTV":71.9424434169,"AccountingUPB":1.0498331513999982E9,"UPB":1.1107022006099968E9,"DefaultUPBHistory":0,"TotalDefault18":8471277.863649497,"TotalLoss24":2910363.9010554748,"ClusterName":"property_type_Bucket:PUD;FactorDate_Bucket:20150301","FICO":744.0622837872,"ObservedMDR":0.0500890316,"FactorDate":20150301,"LoanCount":7218,"WAC":3.9603496885,"DTI":34.5479326682,"NetLossHistory":0,"WAM":66501.9399381329,"TotalDefault12":5851712.095593094,"LTV":72.6774347719,"TotalLoss12":1633464.9969775411,"NetLoss":"","RSModelMDR":0.0500890316,"AvgOrigUPB":286000.3628387367,"AvgLoanSize":227556.2795759059,"TotalLoss18":2356406.622838099},{"DefaultUPB":"","Age":43.5916560278,"TotalDefault24":7.659159340336753E7,"KEY":"property_type_Bucket:SF;FactorDate_Bucket:20150301","CurrentLTV":71.3455613499,"AccountingUPB":1.021189617428996E10,"UPB":1.0609986181109943E10,"DefaultUPBHistory":2949542.88,"TotalDefault18":6.1695010728328355E7,"TotalLoss24":1.9602355488633364E7,"ClusterName":"property_type_Bucket:SF;FactorDate_Bucket:20150301","FICO":743.1691956938,"ObservedMDR":0.0372320171,"FactorDate":20150301,"LoanCount":76608,"WAC":4.2119802683,"DTI":34.0645681747,"NetLossHistory":494471.81342607,"WAM":31340.530061734,"TotalDefault12":4.250818676002976E7,"LTV":72.6075491053,"TotalLoss12":1.094397736820458E7,"NetLoss":"","RSModelMDR":0.0372320171,"AvgOrigUPB":229951.8370982141,"AvgLoanSize":176691.749618804,"TotalLoss18":1.583269852690098E7},{"DefaultUPB":"","Age":81.7154450775,"TotalDefault24":60480.4719230693,"KEY":"property_type_Bucket:Townhouse;FactorDate_Bucket:20150301","CurrentLTV":81.642572334,"AccountingUPB":1326513.9000000001,"UPB":1326513.9000000001,"DefaultUPBHistory":0,"TotalDefault18":48766.236758781,"TotalLoss24":16602.2375726766,"ClusterName":"property_type_Bucket:Townhouse;FactorDate_Bucket:20150301","FICO":679.1200408982,"ObservedMDR":0.2271401022,"FactorDate":20150301,"LoanCount":21,"WAC":5.0359240977,"DTI":38.6068318138,"NetLossHistory":0,"WAM":278.2845549225,"TotalDefault12":33636.1614003823,"LTV":76.2428302637,"TotalLoss12":9243.1512135128,"NetLoss":"","RSModelMDR":0.2271401022,"AvgOrigUPB":182723.0271428571,"AvgLoanSize":147390.4333333333,"TotalLoss18":13393.2366039848}]}}}
```
{: screen}


# Related Links
{: #rellinks notoc}

## API Reference
{: #api}

*  https://www.riskspan.com/rs-edge_api.pdf


## Related Links
{: #general}

* RS Edge: https://www.riskspan.com/rs-edge
* Contact RiskSpan: https://www.riskspan.com/contact-us