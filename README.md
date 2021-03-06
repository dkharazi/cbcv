# cbcv

Most C-suite or senior-level leaders of a firm are interested in knowing the worth or value of their company at any given moment, especially relative to other publicly traded companies. To develop an understanding of this information, the firm must develop a corporate valuation of their company, which represents a process or set of procedures determining the value of the firm. Over the last few decades, there is increasing interest in *customer-based corporate valuation* (or CBCV), which explicitly treats the overall financial valuation of a firm as a function of the value of its customer base.

While there has been a great deal of progress in building a well-validated CBCV model for contractual (or subscription-based) firms in recent years, there hasn't been much progress in building one for noncontractual firms. Non-contractual businesses have more complex transactional patterns because a customer isn't required to notify the business if they decide to churn. Additionally, spend and timing of customer purchases is more irregular across different customers.

Possibly most importantly, there are only a handful of companies who publicly release their customer-level data metrics over time. Most of these customer-level features that could be important in valuing a company are censored for security reasons. Even when a company decides to release these customer-level data metrics, there isn't much consistency in the customer metrics released across companies. In most cases, publicly disclosed data are aggregated over time, making it more difficult to estimate models for customer acquisition, repeat ordering, and spend.

Most of the information is summarized from [McCarthy and Fader's paper about CBCV models](https://deliverypdf.ssrn.com/delivery.php?ID=584095096086108098086117074001002127032069023053024057123008001026070121029099124025037027038012044049023030009125088120010115119094030029067023088007113081095027110038038064024107102069087068084091008114097030077021096088064070088025095071085007010021&EXT=pdf&INDEX=TRUE), so refer to it for additional information and details about the components of a CBCV model. In the paper, the authors aim to develop a CBCV methodology for non-contractual firms. He also outlines some of the most common themes from the paper in [his talk at a marketing conference](https://www.youtube.com/watch?v=ee0etv8RYOM&ab_channel=MASBMarketingAccountabilityStandardsBoard).

# Customer-Based Corporate Valuation Metrics

Corporate valuation is the process of determining the value of a company. Since every dollar of revenue generated by a company must come from its customers, it only makes sense for the valuation of a company to be centered around customer-based metrics. Notably, only a few customer-based corporate valuation (or CBCV) metrics are needed to accurately predict the worth of a company.

Very roughly, revenue comes from either acquired customers or retained customers. In general, companies that do a good job of retaining and developing their customers over time are positioning themselves to increase the worth of their companies in the long run. Specifically, there are six metrics reflecting a company's repeat-purchasing patterns:
- `AU:` Number of active users
- `HAU:` Number of heavy active users
- `F:` Average frequency of orders from active users
- `RR:` Rate of repeat customers
- `RBPO:` Percentage of orders from repeat buyers
- `RBPC:` Percentage of customers who are repeat buyers

Here, `AU` represents the number of customers who've placed at least 1 order in the current year, whereas `HAU` represents the number of customers who've placed at least 2 orders in the current year. Internally, these thresholds act as a good starting points across different types of companies, but could be adjusted based on what a company considers a *heavy active user*. Additionally, the `F` metric represents the average orders placed by active users in the current year.

The `RR` metric represents the percentage of the previous year's buyers who buy again in the current year, relative to all of the previous year's buyers. On a similar note, `RBPO` represents the percentage of the current year's orders from customers with an order in the previous year, relative to all of the current year's orders. Whereas, the `RBPC` metric represents the percentage of of the current year's buyers with an order in the previous year, relative to all of the current year's buyers. In a non-contractual setting, these metrics act as an observable workaround to *retention rate* metrics.

For more information about the accuracy of this small set of customer-based corporate valuation metrics, refer to [Dan McCarthy's slides from his presentation at Wharton](https://scientistcafe.com/CIRUG/2017_07_24ASA_TalkDanMcCarthy.pdf), and refer to [his article](https://www.thetaequity.com/resource/c3/) for illustrations of these metrics. For a deeper understanding of the math behind these metrics and examples of companies using these metrics in practice, refer to [McCarthy and Fader's paper](https://deliverypdf.ssrn.com/delivery.php?ID=217116104122089025069125121097076103121046070053091056099116021109091027113116024081057056103059050003021087120021001116093091000085032086058068011118113065000099106025080050118126124103092083099108005018031018083106115029070123004010092120067092069115&EXT=pdf&INDEX=TRUE). For a deeper dive into modeling customer behavior for both transactional and non-transactional businesses, refer to [McCarthy's dissertation](https://repository.upenn.edu/cgi/viewcontent.cgi?article=4247&context=edissertations).

# Implementing CBCV with Forecasting Models

- FCF = (R(1 ??? VC) ??? FC ??? CAC ?? A)(1 ??? TR)
- FCF is future cash flows
- Here, R is weekly revenue
  - This can be estimated by calculating CLV for all customers then summing it up
  - E[RLV] = average 
- Here, VC is variable costs
- Here, FC is fixed costs
- Here, CAC is customer acquisition cost per customer
- Here, A is gross acquisitions
- Here, TR is tax rate

For a clearer defintion about the differences between residual lifetime values, customer lifetime values, and other customer-based metrics, refer to [McCarthy's slides](https://www.dropbox.com/s/xjak7pezn6i9m06/CLV%20framework.pptx). For an interesting high-level article outlining McCarthy's overall CBCV approach, refer to [this article](https://hbr.org/2020/01/how-to-value-a-company-by-analyzing-its-customers).
