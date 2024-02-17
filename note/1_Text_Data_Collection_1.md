Lab: Text Data Collection (I)
================
Haohan Chen (HKU)
2024-02-17

## Introduction

This notebook demonstrate how to parse text data from common document
format.

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.4.4     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

## Parse PDF files

``` r
if (!require("pdftools")) install.packages("pdftools")
```

    ## Loading required package: pdftools

    ## Using poppler version 23.04.0

``` r
library(pdftools)

# Source: https://www.ceo.gov.hk/archive/5-term/eng/pdf/article20220530.pdf
parsed_pdf = pdftools::pdf_text("data/parse_sample.pdf")

# Check: What is the output like? What is the length and why?
length(parsed_pdf)
```

    ## [1] 8

``` r
print(parsed_pdf)
```

    ## [1] "     Moving Steadily Forward Along Path to Normalcy\n          Amid Stabilised COVID-19 Epidemic\n\n      Having gone through the turbulent time in early March and\nseen the arrival of dawn in April, the fifth wave of the epidemic\nwas clearly under control in May with the daily number of cases\ntested positive hovering between 200 and 300. Nonetheless, to\ncreate favourable conditions for quarantine-free travel with the\nMainland, the Government of the Hong Kong Special\nAdministrative Region (HKSAR) has been steadfastly\nimplementing the strategy of “preventing the importation of cases\nand the resurgence of domestic infections” and striving to reduce\ndeaths, severe cases and infections, while encouraging members\nof the public to receive appropriate COVID-19 vaccine doses in\na timely manner to build a stronger city-wide protection barrier\nagainst the virus. The community can thus be enabled to move\nsteadily forward along a more promising path to normalcy.\n\nEpidemic development\n\n      Over the past few weeks, the daily reported number of cases\ntested positive remained at a low but stagnant level. Neither did\nthe figure continue to drop drastically, nor did it rise considerably\ndespite some infection clusters found. For our peace of mind,\ngenerally low-level figures were observed in May in other\nmonitoring indicators, including the viral load in sewage\nsurveillance tests, the percentage of positive cases found in\nrestriction-testing declaration operations and the percentage of\npositive cases from tests conducted at the community level, as\nwell as the real-time effective reproductive number for local cases\nand COVID-19 point-prevalence rate released by the School of\nPublic Health under The University of Hong Kong.\n"                                                                                                                                                                                                                                                                                                                                                           
    ## [2] "      The drop in confirmed cases, coupled with the multi-tiered\ntriage and treatment strategy in effect, has enabled the public\nhealthcare system to resume its normal operation. The number\nof COVID-19 confirmed cases admitted to public hospitals\nsignificantly decreased from 1 339 on May 1 to 427 on May 29.\nOf the latter, eight were in serious conditions and 13 were in\ncritical conditions (four thereof under intensive care).\n\nGetting society back to normal\n\n      As the epidemic situation remains stable, and the COVID-\n19 vaccination rates of the first and second doses have reached\n92% and 86.9% respectively with the risk of severe or death cases\neffectively reduced among the infected, the HKSAR Government\nhas relaunched social and economic activities on various fronts in\nan orderly manner along the path to normalcy as announced in\nMarch 21 and in response to the expectations from various sectors\nof society. It is particularly gratifying to see that all students\ncity-wide have resumed face-to-face classes at school; the Hong\nKong Diploma of Secondary Education Examination this year has\nbeen conducted successfully; sports premises have been\nreopened; all scheduled premises subject to regulation have\nresumed business; and the catering and retail sectors have reaped\na long-awaited blooming business.            As regards visitors’\nimmigration, further to lifting the flight ban on nine countries in\nApril to allow Hong Kong residents (HKRs) from overseas to\nenter Hong Kong, the HKSAR Government expanded the scope\nto non-HKRs with effect from May 1 alongside suitable\nadjustments made to the route-specific flight suspension\nmechanism. With effect from May 9, the HKSAR Government\nimposed an additional rapid antigen test (RAT) requirement on\n“test-and-hold” at the airport to strengthen the testing\narrangement for inbound passengers on the one hand, while\nshortening their waiting time at the airport to enhance the process\nof closed-loop management from the airport to designated\nquarantine hotels on the other.\n\n\n                                 2\n"
    ## [3] "Implementing third stage of Vaccine Pass as planned\n\n      It has been over 450 days since the launch of the COVID-\n19 Vaccination Programme by the HKSAR Government. No\nshortage of the two COVID-19 vaccines for the people of Hong\nKong has ever occurred, while a growing number of channels for\nvaccination has been provided to bring them more convenience.\nAt present, as many as 100 000 doses can be administered daily,\nwhich can well meet the demand. While the first- and second-\ndose vaccination rates of Hong Kong’s population are\nsatisfactory, the third-dose one has just exceeded 50% and needs\nto be boosted further. With the second stage of the Vaccine Pass\ncoming into effect on April 30, the HKSAR Government will\nimplement the third stage from May 31 onwards as planned.\nPeople will be then generally required to have received three\ndoses before they can enter a series of premises subject to\nregulation.\n\n      In order to strengthen the immune barrier for hospitals and\npublic healthcare facilities, protect members of the public using\npublic healthcare services (especially the elderly and chronic\npatients) and further encourage them to get vaccinated, the\nVaccine Pass arrangement will be implemented by administrative\nmeans in designated healthcare premises under the purview of the\nFood and Health Bureau, the Department of Health and the\nHospital Authority (HA) (such as specialist out-patient clinics of\nHA, Student Health Service Centres and Special Assessment\nCentres, District Health Centres) with effect from June 13.\n\n      Other major anti-epidemic and related measures and events\nare tabulated below in the chronological order:\n\n    Date                      Measure or Event\n\nMay 1          The HKSAR Government adjusted the testing and\n               quarantine requirements for air crew, including\n               subjecting air crew members who are spending a\n\n                                3\n"                                                                                                                                                      
    ## [4] "   Date                 Measure or Event\n\n          short layover in Hong Kong and not entering the\n          local community to a stringent closed-loop\n          arrangement during their stay in Hong Kong, and\n          requiring all air crew members deployed by local\n          airlines for operating flights in and out of Hong\n          Kong to have taken three vaccine doses\n\nMay 1     The HKSAR Government lifted the Outbound\n          Travel Alert issued for COVID-19 on overseas\n          countries/territories\n\nMay 4     The Treatment Centre for COVID-19 at the\n          AsiaWorld-Expo was turned into standby mode\n\nMay 5     The HKSAR Government organised an\n          appreciation and farewell ceremony for the last\n          batch of Mainland medical support team members\n          before their return to the Mainland\n\nMay 6     Twenty-six public hospitals of HA resumed the\n          special visiting arrangement in non-acute wards\n          and units\n\nMay 6     A handover ceremony for the hospital for\n          emergency use constructed with the Central\n          Government’s support at the Lok Ma Chau Loop\n          was held\n\nMay 9     In view of the epidemic development and cost-\n          effectiveness, the HKSAR Government finished\n          turning all the community isolation facilities\n          (CIFs) in Tsing Yi, San Tin, Hong Kong\n          Boundary Crossing Facilities Island of Hong\n          Kong-Zhuhai-Macao Bridge, Fanling, Hung Shui\n          Kiu and Yuen Long to standby mode; it now\n          focuses on the use of Penny’s Bay CIF and a CIF\n\n                          4\n"                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
    ## [5] "   Date                 Measure or Event\n\n          hotel\n\nMay 11    Upon completion of a three-stage outreach\n          vaccination arrangement for residential care\n          homes (RCHs), outreach vaccination had been\n          arranged for the residents of all the 1 100-odd\n          RCHs for the elderly (RCHEs) and RCHs for\n          persons with disabilities (RCHDs) who were\n          suitable for COVID-19 vaccination, largely\n          achieving a comprehensive vaccination coverage\n          with an overall vaccination rate of over 80%\n\nMay 12    Eight Designated Clinics for COVID-19\n          confirmed cases under HA ceased operation and\n          resumed provision of services the next day as\n          General Out-patient Clinics; and another eight\n          ceased operation on May 23 likewise\n\nMay 13    A restricted visiting arrangement was\n          implemented in RCHEs and RCHDs on the\n          premise of observing infection-preventive\n          measures to protect the health of residents and\n          staff of the RCHs\n\nMay 14    The Social Welfare Department returned four\n          sports centres earlier used as holding centres\n          (namely Choi Wing Road Sports Centre, Shek\n          Kip Mei Park Sports Centre, Harbour Road Sports\n          Centre and Tsuen Wan West Sports Centre) to the\n          Leisure and Cultural Services Department\n\nMay 19    The Education Bureau of the HKSAR\n          Government announced that, having regard to the\n          advice of the Centre for Health Protection, the\n          current daily RAT requirement for students and\n\n\n                          5\n"                                                                                                                                                                                                                                                                                                                                                                                                                                                            
    ## [6] "   Date                  Measure or Event\n\n          school staff be extended till late June\n\nMay 20    The HKSAR Government relaunched the online\n          platform for declaration of non-local vaccination\n          records to provide an additional channel for\n          declaring non-local vaccination records alongside\n          boundary control points and designated post\n          offices\n\nMay 21    Having regard to experts’ advice, the HKSAR\n          Government announced that, in addition to\n          persons aged 60 or above in general as earlier\n          permitted, uninfected persons aged 18 to 59 at a\n          higher risk of COVID-19 exposure or with\n          personal needs might choose to receive a fourth\n          COVID-19 vaccine dose\n\nMay 23    The “LeaveHomeSafe” telephone hotline\n          (2626 3066) commenced operation to handle\n          public enquiries on installation or use of the\n          “LeaveHomeSafe” mobile app in areas such as\n          the storing and display of the Vaccine Pass\n\nMay 27    The HKSAR Government announced that\n          six million RAT kits had been distributed for free\n          to persons aged 60 or above through various\n          elderly service units, and that the initiative be\n          extended till the end of June to encourage them to\n          take rapid tests continually for the regular\n          monitoring of their health conditions\n\nMay 29    The HKSAR Government announced, effective\n          from June 1, the fine-tuned pre-departure and\n          post-arrival nucleic acid testing arrangements\n          applicable to persons boarding for Hong Kong\n\n\n                           6\n"                                                                                                                                                                                                                                                                                                                                                                                                                         
    ## [7] "    Date                       Measure or Event\n\n               from overseas places and Taiwan (including an\n               additional compulsory nucleic acid test on the\n               ninth day of arrival in Hong Kong), and the\n               updated penalty to be incurred by airlines for\n               neglecting to verify the required documentation\n               of persons boarding flights for Hong Kong and\n               triggering the route-specific flight suspension\n               mechanism, to reduce the impact on the journeys\n               of persons coming to Hong Kong while\n               continuing to firmly guard against importation of\n               cases\n\nMay 31         HA extended the special visiting arrangement to\n               other acute and specialist hospitals as well as child\n               and adolescent psychiatric wards or units\n\n\nSupporting enterprises and safeguarding jobs\n\n       The HKSAR Government announced in May that the\nseasonally adjusted unemployment rate for February to April this\nyear stood at 5.4%, representing a 0.4 percentage point increase\nas compared with the preceding three-month period.\nNonetheless, the subsiding local epidemic situation and\nprogressive relaxation of social distancing measures, together\nwith the 2022 Employment Support Scheme (2022 ESS) and new\nround of electronic consumption vouchers of $10,000 each to\neligible citizens as announced in the Government Budget this\nyear, would expectedly give a boost to the business of various\nsectors by and large. It is hoped that enterprises could regain\nvitality and retain staff or even hire more, improving the business\nsentiment and promoting economic rebound.\n\n       Earlier on, the HKSAR Government rolled out the fifth and\nsixth rounds of the Anti-epidemic Fund to provide some financial\n\n                                 7\n"                                                                                                                                                                                                                       
    ## [8] "relief to the enterprises and practitioners of various trades affected\ndirectly or indirectly by the fifth wave of the epidemic, as well as\nto the frontline personnel having contributed to anti-epidemic\nefforts such as cleansing workers.           As at May 25, over\n$14 billion was disbursed. The 2022 ESS, which comes with a\nwider coverage, met with overwhelming response. By the\ndeadline of May 12, applications from 176 000 employers\n(involving about 1.66 million employees) and 119 000 self-\nemployed persons were received. They are being processed in\nbatches. As at May 25, the wage subsidies of May were\napproved for 77 000 employers, involving $5.2 billion. These\nemployers had committed to employ about 665 000 people in\nMay; and a one-off subsidy of $8,000 was approved for about\n64 000 self-employed persons, involving over $0.5 billion.\n\nMoving steadily forward along path to normalcy\n\n       The COVID-19 epidemic has been raging across the globe\nfor nearly two and a half years. Hong Kong has not been spared\nand has met with five waves of the epidemic, of which the latest\none triggered by the highly transmissible Omicron mutant strain\nhas overwhelmed our anti-epidemic capacity.                 While\nprogressing along the path to normalcy, we should feel gratified,\nand most grateful, for the timely assistance from the Central\nGovernment and full co-operation by society at large. This is\nthe 28th monthly report on our anti-epidemic efforts, also the last\none in a row, issued by me as the Chief Executive of the HKSAR.\nI wish Hong Kong steady strides continuously along the hard-\nearned path to normalcy, resuming cross-boundary people flows\nin an orderly manner early and reinvigorating the status as Asia’s\nworld city connecting East and West, and new heights scaled\ntherewith under “One Country, Two Systems”.\n\nMrs Carrie Lam\nChief Executive\nHong Kong Special Administrative Region\nMay 30, 2022\n\n                                  8\n"

``` r
# Save parsed text
write(parsed_pdf, "data/parse_sample_out_pdf.txt")
```

## Parse JSON files

``` r
if (!require("jsonlite")) install.packages("jsonlite")
```

    ## Loading required package: jsonlite

    ## 
    ## Attaching package: 'jsonlite'

    ## The following object is masked from 'package:purrr':
    ## 
    ##     flatten

``` r
library(jsonlite)

# Source: https://gist.github.com/hrp/900964
parsed_json = jsonlite::read_json("data/parse_sample.json")
names(parsed_json)
```

    ##  [1] "text"                      "truncated"                
    ##  [3] "in_reply_to_user_id"       "in_reply_to_status_id"    
    ##  [5] "favorited"                 "source"                   
    ##  [7] "in_reply_to_screen_name"   "in_reply_to_status_id_str"
    ##  [9] "id_str"                    "entities"                 
    ## [11] "contributors"              "retweeted"                
    ## [13] "in_reply_to_user_id_str"   "place"                    
    ## [15] "retweet_count"             "created_at"               
    ## [17] "retweeted_status"          "user"                     
    ## [19] "id"                        "coordinates"              
    ## [21] "geo"

``` r
# Example: Get tweet text
parsed_json$text
```

    ## [1] "RT @PostGradProblem: In preparation for the NFL lockout, I will be spending twice as much time analyzing my fantasy baseball team during ..."

## Parse XML files

``` r
if (!require("xml2")) install.packages("xml2")
```

    ## Loading required package: xml2

``` r
library(xml2)

# Source: https://www.irs.gov/charities-non-profits/form-990-series-downloads
parsed_xml = xml2::read_xml("data/parse_sample.xml")
parsed_xml_ls = xml2::as_list(parsed_xml) # Make the parsed XML object a list
```

``` r
# Example: Get address
parsed_xml_ls$Return$ReturnData$IRS990$USAddress
```

    ## $AddressLine1Txt
    ## $AddressLine1Txt[[1]]
    ## [1] "1906 BLAKE AVENUE"
    ## 
    ## 
    ## $CityNm
    ## $CityNm[[1]]
    ## [1] "GLENWOOD SPRINGS"
    ## 
    ## 
    ## $StateAbbreviationCd
    ## $StateAbbreviationCd[[1]]
    ## [1] "CO"
    ## 
    ## 
    ## $ZIPCd
    ## $ZIPCd[[1]]
    ## [1] "81601"

``` r
# Example: Get activity or mission statement
parsed_xml_ls$Return$ReturnData$IRS990$ActivityOrMissionDesc
```

    ## [[1]]
    ## [1] "TO BE THE LEADER FOR EXCELLENCE IN PERSONALIZED CARE AND HEALING."

## Parse HTML files

``` r
library(xml2)

# Source: https://www.info.gov.hk/gia/general/202206/21/P2022062100598.htm
parsed_html = xml2::read_html("data/parse_sample.html")
print(parsed_html)
```

    ## {html_document}
    ## <html>
    ## [1] <head>\n<meta http-equiv="X-UA-Compatible" content="IE=edge">\n<meta http ...
    ## [2] <body>\r\n\t<a id="skiptocontent" href="#contentBody" class="access">Go t ...

``` r
# Example: Get ALL the text from this webpage
parsed_html_text = xml2::xml_text(parsed_html)
# Check the output. What's not great?
print(parsed_html_text)
```

    ## [1] "Speech by CE at HKEX 22nd Anniversary Celebrations (English only) (with photos/video)\r\n\t\r\n\t$(function()\r\n\t{\t\r\n\t\tvar url = 'select_en.htm?' + Math.random()*Math.random();\r\n\t\t$(\"#includedContent\").load(url,function(){\r\n\t\t\t$('#selectManual option[value=\"P2022062100598\"]').attr(\"selected\", \"selected\");\t\t\r\n\t\t}); \r\n\t\t$(\"#rightContent\").clone().appendTo(\".controlDisplay2\");\r\n\t});\r\n\t\r\n\tfunction handleSelect()\r\n\t{\r\n\t\tvar x = document.getElementById(\"selectManual\").selectedIndex;\r\n\t\twindow.location = document.getElementsByTagName(\"option\")[x].value+\".htm\";\r\n\t}\t\t\r\n\t\r\n\tGo to main content\r\n\t\r\n\t\t$(document).ready(function () {\r\n\t\t\tresizeStarDivider('E');\r\n\t\t\tif ((/iPhone|iPod|iPad|Android|BlackBerry/).test(navigator.userAgent)) {\r\n\t\t\t\t$(\".icon_save\").css(\"display\",\"none\");\r\n\t\t\t};\r\n\t\t});\r\n\t\r\n\t\t\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\tBrand HK\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\r\n\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\t | Font Size: \r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t | Sitemap\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\r\n\t\t\t\r\n\t\t\r\n\t\r\n\r\n\r\n  \r\n\r\n\r\n\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t \r\n\t\t\t\t\r\n\t\t\t\t\tSpeech by CE at HKEX 22nd Anniversary Celebrations (English only) (with photos/video)\r\n\t\t\t\t\t\r\n\t\t\t\t\t\tSpeech by CE at HKEX 22nd Anniversary Celebrations (English only) (with photos/video)\r\n\t\t\t\t\t\r\n\t\t\t\t\t*************************************************************************************\r\n\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t     Following is the speech by the Chief Executive, Mrs Carrie Lam, at the Hong Kong Exchanges and Clearing Limited 22nd Anniversary Celebrations today (June 21):\r\nCommissioner Liu (Commissioner of the Ministry of Foreign Affairs of the People's Republic of China in the Hong Kong Special Administrative Region (HKSAR), Mr Liu Guangyuan), Laura (Chairman of the Hong Kong Exchanges and Clearing Limited (HKEX), Mrs Laura Cha), Nicolas (Chief Executive Officer of HKEX, Mr Nicolas Aguzin), all HKEX Board members, ladies and gentlemen,\r\n     Good afternoon. It gives me great pleasure to join you today in celebration of HKEX's 22nd anniversary. And a warm welcome to all HKEX partners and friends joining online for this happy occasion.\r\n     Today's anniversary gathering takes on added significance with the reopening of the HKEX Connect Hall. The newly renovated Connect Hall has been fitted out with the latest technology, as well as a brand-new multi-function venue, the 388 Suite, and standout features like the eye-catching Brand, Media and Gong Walls. To say the least, the smartly refurbished Connect Hall will continue to link global markets and our financial community, while serving as an inspiring symbol of one of the world's largest financial centres. And if I may add, today's gathering also carries a third meaning, that is, you will see a lady Chief Executive and a lady Chairperson of HKEX striking the gong for perhaps the final time, because I doubt very much we will have this happy coincidence of a lady Chief Executive and a lady Chairperson of HKEX for some time to come. And if one takes into account that Laura and I came from the same secondary school, we've served on ExCo (Executive Council) for 10 years and we are good personal friends, this thing will never happen.\r\n     HKEX plays a pivotal role in fostering the internationalisation of Hong Kong's financial centre and the city per se. To date, Hong Kong is a major listing platform from different jurisdictions. Alongside a vibrant securities market, HKEX's vision to go international is evidenced by its acquisition as early as 2012 of the London Metal Exchange, commonly known as LME, which until now remains a world centre for the trading of industrial metals where the majority of all non-ferrous metal futures business is transacted among participants from the physical industry and the financial community.\r\n     I very much treasure HKEX's strong partnership with the HKSAR Government during these five years, especially during my previous two trips to Davos in 2019 and 2020 for attending the World Economic Forum (WEF). HKEX not only greatly assisted us in organising the signature Hong Kong Night to introduce to guests from around the world Hong Kong's unique strengths and abounding opportunities, but also actively made use of various occasions like the WEF Annual Meetings and media interviews to promote Hong Kong's cosmopolitan outlook. This year, I was unable to lead a government delegation to Davos for WEF taking place in May, after last year's edition was cancelled due to the epidemic, given the need to ensure a smooth transition to the new-term Government; I felt much encouraged that Laura and Nicolas led an HKEX delegation to physically participate in over 70 meetings, events and media interviews in order to connect with global leaders and champion Hong Kong's vibrant capital markets for us. I was particularly thrilled to have heard from Nicolas during his recent interview from Davos that HKEX is planning to establish two international offices, alongside its footprints in Singapore, Beijing and Shanghai at present, to reach out to more overseas investors and market Hong Kong as a fundraising destination.\r\n     Despite COVID-19, social unrest and significant economic and geopolitical factors, HKEX, together with the HKSAR Government, has worked assiduously to build on Hong Kong's singular advantages under the \"One Country, Two Systems\" principle. The revamp of the Hong Kong listing regime in 2018 has realised outsized dividends, attracting new economy companies with weighted voting rights, as well as making Hong Kong Asia's largest, and the world's second-largest, fundraising hub for biotechnology. More recently, the reform relating to special purpose acquisition companies, better known as SPACs, has helped to enhance our competitiveness and forge a more diverse, dynamic and sustainable listing regime.\r\n     With the unwavering support from the Central Government, our various mutual market access initiatives have thrived. Some of you may recall that I attended the launch ceremony of Bond Connect here on my third day as the Chief Executive. Since then, we have witnessed the launch of the Bond Connect southbound trading, the cross-boundary Wealth Management Connect and A-share index futures, and we are about to welcome exchange-traded funds, or ETFs, to be included under Stock Connect. Each of them has expanded mutual access between the financial markets of Hong Kong and the Mainland, realising fresh investment opportunities for all concerned.\r\n     When it comes to creating opportunities, I am pleased to have seen HKEX's new strategic plan and its vision to create the \"Marketplace of the Future\". Among the plan's three pillars is an ambitious, long-term blueprint built on \"connecting China and the world\". That means expanding Connect programmes, becoming the Mainland's offshore risk-management centre, solidifying HKEX's role as the Mainland's preferred offshore fundraising centre, and increasing its portfolio of Mainland product offerings. In strengthening Hong Kong's unique position as a conduit for capital flow between the Mainland and the world, HKEX's strategy aligns seamlessly with the National 14th Five-Year Plan, which champions the reinforcing of Hong Kong's status as a global financial centre.\r\n     I am also delighted to learn about HKEX's ever-growing commitment to driving sustainability. In March this year, Hong Kong's first carbon futures ETF was listed on HKEX, extending the coverage of Hong Kong-listed commodity ETFs to carbon credits, an integral asset class in the global drive to achieving carbon neutrality. Looking at the Guangdong-Hong Kong-Macao Greater Bay Area (GBA), HKEX has been forging collaboration with various Mainland partners to press ahead with green and sustainable finance. To name a few, HKEX entered into a memorandum of understanding (MoU) with the Guangzhou Futures Exchange last August to drive a green and low-carbon market in GBA, and another MoU with the Guangzhou-based China Emissions Exchange in March this year to strengthen co-operation in carbon finance, including exploring the development of a voluntary carbon emission reduction programme in GBA. These joint efforts will gainfully add to our country's endeavours to peak carbon emissions and reach carbon neutrality.\r\n     As the first lady Chief Executive of the HKSAR, I am particularly happy with HKEX's commitment in championing for diversity on the boards of listed companies. Under the amended Corporate Governance Code and Listing Rules of the Stock Exchange of Hong Kong, with effect from January 1 this year, existing listed issuers have a three-year transition period to comply with the diverse board requirement, that is to appoint a director of a different gender no later than December 31, 2024, whereas IPO applicants have to identify at least a director of a different gender from July 1, 2022, onwards.\r\n     As my five-year plan is drawing to a close, I would like to take this opportunity to remind us all that maintaining Hong Kong's status as an international financial centre is actually a requirement stipulated in Article 109 of the Basic Law. While the Basic Law has also bestowed upon the HKSAR the key factors of success, namely no foreign exchange control policies and the free flow of capital within, into and out of the SAR (Article 112), it is incumbent upon us to enhance our competitiveness through putting due emphasis on a sound regulatory system and market development. That is why a Financial Leaders Forum was created at the beginning of this term of Government to enable the Government to play a more active role on policymaking and matters relating to monetary stability, financial safety and regulation as well as market development. I wish to take this opportunity to thank the Financial Secretary for chairing the Financial Leaders Forum all these years, and stability has been assured with his re-appointment and the re-appointment of Chris Hui (Secretary for Financial Services and the Treasury, Mr Christopher Hui) as the leaders of the financial services in the HKSAR Government.\r\n     Finally, I would like to express my deepest gratitude to Laura and Gucho (Mr Aguzin), if I may call you that, and to each and every one of you, for the remarkable contributions in achieving an orderly and sustainable growth of Hong Kong's securities market. My gratitude also goes to all members of the Financial Leaders Forum and the Financial Services Development Council for their dedication and support over the past five years. I have every confidence that HKEX will continue to be a pivotal player in taking Hong Kong's financial services sector to new heights, locally and beyond.\r\n     Thank you very much.\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t \r\n\t\t\t\tEnds/Tuesday, June 21, 2022\r\n\t\t\t\t\r\n\t\t\t\t Issued at HKT 20:16\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t NNNN\r\n\t\t\t\t\t \r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\tArchives  \r\n\t\t\t\t\t\t\tYesterday's Press Releases  \r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\t\tBack to Index Page\r\n\t\t\t\t\t\t\t\r\n\t\t\t\t\t\t\tBack to top\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\tToday's Press Releases  \r\n\t\t\t\t\r\n\t\t\t\r\n\t\t\r\n\t\t\r\n\t\t\t\r\n\t\t\t  \r\n\t\t\t\t\r\n\t\t\t\tPhoto\r\n\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t  Audio / Video\r\n\t\t\t  \r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\tCE attends HKEX 22nd Anniversary Celebrations\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\tView\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t\t\r\n\t\t\t\t\t \r\n\t\t\t\t\t\r\n\t\t\t  \r\n\t\t\t  \r\n\t\t\t  \r\n\r\n\t\t\t\r\n\t\t\t\r\n\t\t\r\n\t\r\n\r\n\r\n\t\r\n\t\t\r\n\t\t\t\r\n\t\t\t\t\r\n\t\t\t\t\r\n\t\t\t\r\n\t\t\t\r\n\t\r\n\r\n\r\n\r\n$(\".fancybox\").fancybox({\r\n\twrapCSS    : 'fancybox-custom',\r\n\tcloseClick : false,\r\n\tloop:true,\r\n\topenEffect : 'none',\r\n\r\n\thelpers : {\r\n\t\ttitle : {\r\n\t\t\ttype : 'inside'\r\n\t\t},\r\n\t\toverlay : {closeClick: true}\r\n\t},\r\n\r\n\tafterLoad : function() {\r\n\t\tvar sp = arguments[0].href;\r\n\t\tvar tmpStr = this.title.replace(new RegExp('\\\"','gm'),\"&quot;\")\r\n        \t\t\t\t\t  .replace(new RegExp('\\'','gm'),\"&#39\")  \t\t\t\t\t\t      \r\n\t\t\t\t\t\t\t  .replace(new RegExp('>','gm'),'&gt;')\r\n\t                          .replace(new RegExp('<','gm'),'&lt;')\r\n\t\t\t\t\t\t\t  .replace(new RegExp('\\r\\n','gm'),'<br/>')\r\n                              .replace(new RegExp('\\n','gm'),'<br/>')\r\n\t                          .replace(new RegExp('\\r','gm'),'<br/>');\r\n\t\t\r\n\t\tthis.title = '<table><tr><td>' + tmpStr + '</td></tr></table>';\r\n\t}\r\n});\r\n\r\n\r\n"

``` r
# Example: Only get text from webpage sections you want
# Note: You need to analyze the webpage to locate the sections of interest.
# A handy Google Chrome extension: SelectorGadget

parsed_html_speech = parsed_html %>% 
  xml_find_all('//*[(@id = "pressrelease")]') %>%
  xml_text()

parsed_html_title = parsed_html %>%
  xml_find_all('//*[(@id = "PRHeadlineSpan")]') %>%
  xml_text()
```

<figure>
<img src="images/image-695647128.png"
alt="A screenshot showing how I identify sections of interest on the webpage using SelectorGadget in Google Chrome" />
<figcaption aria-hidden="true">A screenshot showing how I identify
sections of interest on the webpage using <code>SelectorGadget</code> in
Google Chrome</figcaption>
</figure>

``` r
# Save the parsed text
write(parsed_html_speech, "data/parse_sample_out_html_speech.txt")
write(parsed_html_title, "data/parse_sample_out_html_title.txt")
```
