# utl-validation-and-verification-of-table-data
Validation and verification of table data 

    SAS Forum: Validation and verification of table data                                                                                                                    
                                                                                                                                                                            
    github                                                                                                                                                                  
    https://tinyurl.com/yzhbsr97                                                                                                                                            
    https://github.com/rogerjdeangelis/utl-validation-and-verification-of-table-data                                                                                        
                                                                                                                                                                            
    https://github.com/rogerjdeangelis/voodoo                                                                                                                               
                                                                                                                                                                            
    sas forum                                                                                                                                                               
    https://communities.sas.com/t5/New-SAS-User/How-to-analyze-dataset/m-p/604260                                                                                           
                                                                                                                                                                            
    macros                                                                                                                                                                  
    https://tinyurl.com/y9nfugth                                                                                                                                            
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                                                                              
                                                                                                                                                                            
    *_                   _                                                                                                                                                  
    (_)_ __  _ __  _   _| |_                                                                                                                                                
    | | '_ \| '_ \| | | | __|                                                                                                                                               
    | | | | | |_) | |_| | |_                                                                                                                                                
    |_|_| |_| .__/ \__,_|\__|                                                                                                                                               
            |_|                                                                                                                                                             
    ;                                                                                                                                                                       
                                                                                                                                                                            
    data have;                                                                                                                                                              
           length acctno $13  deactreason $4 dealertype $2 Province $2;                                                                                                     
           infile datalines dsd delimiter = '|';                                                                                                                            
           format actdt mmddyy10. deactdt mmddyy10. sales dollar8.0;                                                                                                        
           informat actdt mmddyy10. deactdt mmddyy10. sales dollar8.0;                                                                                                      
           input acctno $ actdt deactdt deactreason $ goodcredit rateplan dealertype $ AGE Province $ sales;                                                                
                                                                                                                                                                            
    cards4;                                                                                                                                                                 
    1176913194483|06/20/1999|||0|1|A1|58|BC|128                                                                                                                             
    1176914599423|10/04/1999|10/15/1999|NEED|1|1|A1|45|AB|72                                                                                                                
    1176951913656|07/01/2000|||0|1|A1|57|BC|593                                                                                                                             
    1176954000288|05/30/2000|||1|2|A1|47|ON|83                                                                                                                              
    1176969186303|12/13/2000|||1|1|C1|82|BC|                                                                                                                                
    1176991056273|08/31/1999|09/18/2000|MOVE|1|1|C1|92|QC|1041                                                                                                              
    1176991866552|05/24/2000|||1|1|A1|77|ON|                                                                                                                                
    1176992889500|11/28/2000|||1|1|C1|68|AB|72                                                                                                                              
    1177000067271|12/23/1999|||0|1|B1|75|ON|134                                                                                                                             
    1177010940613|12/09/1999|||1|2|A1|42|NS|11                                                                                                                              
    1177025997013|11/09/1999|||1|1|A1|26|BC|154                                                                                                                             
    1177027515760|10/19/1999|||1|1|B1|73|BC|16                                                                                                                              
    1177028996676|09/21/2000|||0|1|C1||QC|179                                                                                                                               
    1177038747105|03/14/2000|||0|1|C1|41|ON|705                                                                                                                             
    1177045857516|06/22/2000|||1|1|A1|53|QC|83                                                                                                                              
    1177057406016|09/21/2000|||0|1|C1|50|ON|529                                                                                                                             
    1177066422248|04/26/1999|01/15/2001|NEED|0|1|A2|55|NS|44                                                                                                                
    ;;;;                                                                                                                                                                    
    run;                                                                                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
    Up to 40 obs from HAVE total obs=17                                                                                                                                     
                                                                                                                                                                            
    Obs       ACCTNO        DEACTREASON    DEALERTYPE    PROVINCE    ACTDT    DEACTDT    SALES    GOODCREDIT    RATEPLAN    AGE                                             
                                                                                                                                                                            
      1    1176913194483                       A1           BC       14415         .       128         0            1        58                                             
      2    1176914599423       NEED            A1           AB       14521     14532        72         1            1        45                                             
      3    1176951913656                       A1           BC       14792         .       593         0            1        57                                             
      4    1176954000288                       A1           ON       14760         .        83         1            2        47                                             
      5    1176969186303                       C1           BC       14957         .         .         1            1        82                                             
      6    1176991056273       MOVE            C1           QC       14487     14871      1041         1            1        92                                             
      7    1176991866552                       A1           ON       14754         .         .         1            1        77                                             
      8    1176992889500                       C1           AB       14942         .        72         1            1        68                                             
      9    1177000067271                       B1           ON       14601         .       134         0            1        75                                             
     10    1177010940613                       A1           NS       14587         .        11         1            2        42                                             
     11    1177025997013                       A1           BC       14557         .       154         1            1        26                                             
     12    1177027515760                       B1           BC       14536         .        16         1            1        73                                             
     13    1177028996676                       C1           QC       14874         .       179         0            1         .                                             
     14    1177038747105                       C1           ON       14683         .       705         0            1        41                                             
     15    1177045857516                       A1           QC       14783         .        83         1            1        53                                             
     16    1177057406016                       C1           ON       14874         .       529         0            1        50                                             
     17    1177066422248       NEED            A2           NS       14360     14990        44         0            1        55                                             
                                                                                                                                                                            
    *            _               _                                                                                                                                          
      ___  _   _| |_ _ __  _   _| |_                                                                                                                                        
     / _ \| | | | __| '_ \| | | | __|                                                                                                                                       
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                                                        
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                                                       
                    |_|                                                                                                                                                     
    ;                                                                                                                                                                       
                                                                                                                                                                            
    ANSWER These questions and more                                                                                                                                         
                                                                                                                                                                            
    a. The number of activated and deactivated accounts?                                                                                                                    
    b. When is the earliest and latest activation and deactivation dates available?                                                                                         
    c. When is the earliest and latest activation and deactivation dates available?                                                                                         
                                                                                                                                                                            
    *                                                                                                                                                                       
      __ _                                                                                                                                                                  
     / _` |                                                                                                                                                                 
    | (_| |                                                                                                                                                                 
     \__,_|                                                                                                                                                                 
                                                                                                                                                                            
    ;                                                                                                                                                                       
                                                                                                                                                                            
    a. The number of activated and deactivated accounts? (17,3 respetively)                                                                                                 
                                                                                                                                                                            
                           N                                                                                                                                                
    Variable       N    Miss         Minimum         Maximum            Mean          Median         Std Dev             Sum                                                
    ------------------------------------------------------------------------------------------------------------------------                                                
    ACTDT         17       0        14360.00        14957.00        14675.47        14683.00     183.9232577       249483.00                                                
    DEACTDT        3      14        14532.00        14990.00        14797.67        14871.00     237.6432901        44393.00                                                
                                                                                                                                                                            
    *_                                                                                                                                                                      
    | |__                                                                                                                                                                   
    | '_ \                                                                                                                                                                  
    | |_) |                                                                                                                                                                 
    |_.__/                                                                                                                                                                  
                                                                                                                                                                            
    ;                                                                                                                                                                       
    b. When is the earliest and latest activation and deactivation dates available?                                                                                         
                                                                                                                                                                            
       Univariate distribution of ACTDT (   ) values                                                                                                                        
        Distinct values: 16                                                                                                                                                 
        Format in dataset:  MMDDYY10.                                                                                                                                       
        -----------------------------------------------------------------                                                                                                   
                                                                                                                                                                            
        n            17                              min       04/26/1999  earliest                                                                                         
        nmiss         0                              P1        04/26/1999                                                                                                   
                                                     P5        04/26/1999                                                                                                   
        mean                 03/06/2000              P10       06/20/1999                                                                                                   
        std - days                  183.92           Q1        10/19/1999                                                                                                   
        std - years                   0.50           median    03/14/2000                                                                                                   
                                                     Q3        07/01/2000                                                                                                   
        range - days                597              P90       11/28/2000                                                                                                   
        range - years                 1.64           P95       12/13/2000                                                                                                   
                                                     P99       12/13/2000                                                                                                   
        Q1-Q3 - days                256              max       12/13/2000  latest                                                                                           
        Q1-Q3 - years                 0.70                                                                                                                                  
                                                                                                                                                                            
       Univariate distribution of DEACTDT (   ) values                                                                                                                      
        Distinct values: 3                                                                                                                                                  
        Format in dataset:  MMDDYY10.                                                                                                                                       
        -----------------------------------------------------------------                                                                                                   
                                                                                                                                                                            
        n             3                              min       10/15/1999  earliest                                                                                         
        nmiss        14                              P1        10/15/1999                                                                                                   
                                                     P5        10/15/1999                                                                                                   
        mean                 07/06/2000              P10       10/15/1999                                                                                                   
        std - days                  237.64           Q1        10/15/1999                                                                                                   
        std - years                   0.65           median    09/18/2000                                                                                                   
                                                     Q3        01/15/2001                                                                                                   
        range - days                458              P90       01/15/2001                                                                                                   
        range - years                 1.25           P95       01/15/2001                                                                                                   
                                                     P99       01/15/2001                                                                                                   
        Q1-Q3 - days                458              max       01/15/2001  latest                                                                                           
        Q1-Q3 - years                 1.25                                                                                                                                  
                                                                                                                                                                            
    *                                                                                                                                                                       
      ___                                                                                                                                                                   
     / __|                                                                                                                                                                  
    | (__                                                                                                                                                                   
     \___|                                                                                                                                                                  
                                                                                                                                                                            
    ;                                                                                                                                                                       
    c. What is the age and province distributions of active and deactivated customers? (Use dashboards)                                                                     
                                                                                                                                                                            
    TOP 60 ALL PAIRS OF VARIABLES WHERE MAX LEVELS IS 2000 AND MAX NUMBER OF VARIABLES IS 30                                                                                
     actdt * AGE top 60 frequent                                                                                                                                            
                                                                                                                                                                            
    Obs      ACTDT       AGE    COUNT    PERCENT                                                                                                                            
                                                                                                                                                                            
      1    10/19/1999     73      1      5.88235                                                                                                                            
      2    08/31/1999     92      1      5.88235                                                                                                                            
      3    05/30/2000     47      1      5.88235                                                                                                                            
      4    11/28/2000     68      1      5.88235                                                                                                                            
      5    07/01/2000     57      1      5.88235                                                                                                                            
      6    05/24/2000     77      1      5.88235                                                                                                                            
      7    10/04/1999     45      1      5.88235                                                                                                                            
      8    03/14/2000     41      1      5.88235                                                                                                                            
      9    11/09/1999     26      1      5.88235                                                                                                                            
     10    06/20/1999     58      1      5.88235                                                                                                                            
     11    12/09/1999     42      1      5.88235                                                                                                                            
     12    12/23/1999     75      1      5.88235                                                                                                                            
     13    09/21/2000      .      1      5.88235                                                                                                                            
     14    09/21/2000     50      1      5.88235                                                                                                                            
     15    04/26/1999     55      1      5.88235                                                                                                                            
     16    06/22/2000     53      1      5.88235                                                                                                                            
     17    12/13/2000     82      1      5.88235                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    TOP 60 ALL PAIRS OF VARIABLES WHERE MAX LEVELS IS 2000 AND MAX NUMBER OF VARIABLES IS 30                                                                                
     actdt * Province top 60 frequent                                                                                                                                       
                                                                                                                                                                            
    Obs      ACTDT       PROVINCE    COUNT    PERCENT                                                                                                                       
                                                                                                                                                                            
      1    10/19/1999       BC         1      5.88235                                                                                                                       
      2    08/31/1999       QC         1      5.88235                                                                                                                       
      3    05/30/2000       ON         1      5.88235                                                                                                                       
      4    11/28/2000       AB         1      5.88235                                                                                                                       
      5    07/01/2000       BC         1      5.88235                                                                                                                       
      6    05/24/2000       ON         1      5.88235                                                                                                                       
      7    10/04/1999       AB         1      5.88235                                                                                                                       
      8    03/14/2000       ON         1      5.88235                                                                                                                       
      9    11/09/1999       BC         1      5.88235                                                                                                                       
     10    06/20/1999       BC         1      5.88235                                                                                                                       
     11    12/09/1999       NS         1      5.88235                                                                                                                       
     12    12/23/1999       ON         1      5.88235                                                                                                                       
     13    09/21/2000       ON         1      5.88235                                                                                                                       
     14    09/21/2000       QC         1      5.88235                                                                                                                       
     15    04/26/1999       NS         1      5.88235                                                                                                                       
     16    06/22/2000       QC         1      5.88235                                                                                                                       
     17    12/13/2000       BC         1      5.88235                                                                                                                       
                                                                                                                                                                            
                                                                                                                                                                            
    TOP 60 ALL PAIRS OF VARIABLES WHERE MAX LEVELS IS 2000 AND MAX NUMBER OF VARIABLES IS 30                                                                                
     deactdt * AGE top 60 frequent                                                                                                                                          
                                                                                                                                                                            
    Obs       DEACTDT    AGE    COUNT    PERCENT                                                                                                                            
                                                                                                                                                                            
      1             .     75      1      5.88235                                                                                                                            
      2             .     68      1      5.88235                                                                                                                            
      3             .     50      1      5.88235                                                                                                                            
      4             .     82      1      5.88235                                                                                                                            
      5             .     58      1      5.88235                                                                                                                            
      6             .     47      1      5.88235                                                                                                                            
      7             .     73      1      5.88235                                                                                                                            
      8             .     41      1      5.88235                                                                                                                            
      9             .     77      1      5.88235                                                                                                                            
     10             .     53      1      5.88235                                                                                                                            
     11    01/15/2001     55      1      5.88235                                                                                                                            
     12    10/15/1999     45      1      5.88235                                                                                                                            
     13             .      .      1      5.88235                                                                                                                            
     14             .     26      1      5.88235                                                                                                                            
     15             .     42      1      5.88235                                                                                                                            
     16             .     57      1      5.88235                                                                                                                            
     17    09/18/2000     92      1      5.88235                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    TOP 60 ALL PAIRS OF VARIABLES WHERE MAX LEVELS IS 2000 AND MAX NUMBER OF VARIABLES IS 30                                                                                
     deactdt * Province top 60 frequent                                                                                                                                     
                                                                                                                                                                            
    Obs       DEACTDT    PROVINCE    COUNT    PERCENT                                                                                                                       
                                                                                                                                                                            
     1              .       BC         5      29.4118                                                                                                                       
     2              .       ON         5      29.4118                                                                                                                       
     3              .       QC         2      11.7647                                                                                                                       
     4     01/15/2001       NS         1       5.8824                                                                                                                       
     5     09/18/2000       QC         1       5.8824                                                                                                                       
     6              .       NS         1       5.8824                                                                                                                       
     7              .       AB         1       5.8824                                                                                                                       
     8     10/15/1999       AB         1       5.8824                                                                                                                       
                                                                                                                                                                            
                                                                                                                                                                            
    *          _       _   _                                                                                                                                                
     ___  ___ | |_   _| |_(_) ___  _ __                                                                                                                                     
    / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                                                    
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                                                                   
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                                                                   
                                                                                                                                                                            
    ;                                                                                                                                                                       
                                                                                                                                                                            
    %inc "c:/oto/oto_voodoo.sas";                                                                                                                                           
                                                                                                                                                                            
    %utlvdoc                                                                                                                                                                
        (                                                                                                                                                                   
        libname        = work         /* libname of input dataset */                                                                                                        
        ,data          = have         /* name of input dataset */                                                                                                           
        ,key           = acctno       /* 0 or variable */                                                                                                                   
        ,ExtrmVal      = 5            /* display top and bottom 30 frequencies */                                                                                           
        ,UniPlot       = 1            /* 'true' enables ('false' disables) plot option on univariate output */                                                              
        ,UniVar        = 1            /* 'true' enables ('false' disables) plot option on univariate output */                                                              
        ,misspat       = 1            /* 0 or 1 missing patterns */                                                                                                         
        ,chart         = 1            /* 0 or 1 line printer chart */                                                                                                       
        ,taball        = acctno actdt deactdt deactreason goodcredit rateplan dealertype AGE Province sales /* variable 0 */                                                
        ,tabone        = actdt        /* 0 or  variable vs all other variables          */                                                                                  
        ,mispop        = 1            /* 0 or 1  missing vs populated*/                                                                                                     
        ,mispoptbl     = 1            /* 0 or 1  missing vs populated*/                                                                                                     
        ,dupcol        = 1            /* 0 or 1  columns duplicated  */                                                                                                     
        ,unqtwo        = acdt goodcredit rateplan dealertype  AGE Province           /* 0 */                                                                                
        ,vdocor        = 1            /* 0 or 1  correlation of numeric variables */                                                                                        
        ,oneone        = 1            /* 0 or 1  one to one - one to many - many to many */                                                                                 
        ,cramer        = 1            /* 0 or 1  association of character variables    */                                                                                   
        ,optlength     = 1                                                                                                                                                  
        ,maxmin        = 1                                                                                                                                                  
        ,unichr        = 1                                                                                                                                                  
        ,outlier       = 1                                                                                                                                                  
        ,printto       = d:\txt\vdo\&data..txt        /* file or output if output window */                                                                                 
        ,Cleanup       = 0           /* 0 or 1 delete intermediate datasets */                                                                                              
        );                                                                                                                                                                  
                                                                                                                                                                            
    *                                                        _                                                                                                              
     _ __ ___   ___  _ __ ___    _____  _____ ___ _ __ _ __ | |_ ___                                                                                                        
    | '_ ` _ \ / _ \| '__/ _ \  / _ \ \/ / __/ _ \ '__| '_ \| __/ __|                                                                                                       
    | | | | | | (_) | | |  __/ |  __/>  < (_|  __/ |  | |_) | |_\__ \                                                                                                       
    |_| |_| |_|\___/|_|  \___|  \___/_/\_\___\___|_|  | .__/ \__|___/                                                                                                       
                                                      |_|                                                                                                                   
    ;                                                                                                                                                                       
                                                                                                                                                                            
    Saome other excerpts                                                                                                                                                    
                                                                                                                                                                            
    You may need ans inexpensive power worstation or lap top for thia.                                                                                                      
    Man solitary confinement (VM) EG host cannot run this on even small tables (<10gb)                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
    DATA VERIFICATION + VALIDATION FOR WORK.HAVE                                                                                                                            
    have                                                                                                                                                                    
    Dataset summary for WORK.HAVE                                                                                                                                           
                                                                                                                                                                            
        Observations:       17                                                                                                                                              
        Variables:          10                                                                                                                                              
        ----------------------------------------                                                                                                                            
                                                                                                                                                                            
        Variables by type:                                                                                                                                                  
        -------------------                                                                                                                                                 
           Numeric:        6                                                                                                                                                
             Quantity:          4                                                                                                                                           
             Date/Time:         2                                                                                                                                           
                                                                                                                                                                            
           Character:      4                                                                                                                                                
        =========================                                                                                                                                           
                                                                                                                                                                            
                                                                                                                                                                            
        Missing or uniformly evaluated variables:                                                                                                                           
        ------------------------------------------                                                                                                                          
          - missing for all observations:      0                                                                                                                            
          - uniformly evaluated -- all:        0                                                                                                                            
              with one or more missing values:      0                                                                                                                       
              with no missing values:               0                                                                                                                       
        ==================================================                                                                                                                  
                                                                     | Interpretation                                                                                       
                                                                     |                                                                                                      
     #     Variable      Unique Values     Type    Length  Format    |                                                                                                      
    ---    --------      -------------     ----    ------  ------    |                                                                                                      
                                                                     |                                                                                                      
      1    ACCTNO                  17      char     13               | Unique primary key (same as the number og obd above)                                                 
      2    ACTDT                   16      num       8     MMDDYY10. | One duplicate acdt                                                                                   
      3    AGE                     16      num       8               | One duplicate age                                                                                    
      4    DEACTDT                  3      num       8     MMDDYY10. | Three distinct deactivation dates                                                                    
      5    DEACTREASON              2      char      4               | Three distinct deactivation reasons                                                                  
      6    DEALERTYPE               4      char      2               | Four distinct dealer types                                                                           
      7    GOODCREDIT               2      num       8               | Two distinct levels of credit                                                                        
      8    PROVINCE                 5      char      2               | Five distinct provinces                                                                              
      9    RATEPLAN                 2      num       8               | Two unique rateplans                                                                                 
     10    SALES                   13      num       8     DOLLAR8.  | Thirteen distinct dollar sales                                                                       
                                                                     |                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
     DEACTREASON    Frequency     Percent                                                                                                                                   
     ------------------------------------                                                                                                                                   
                          14       82.35                                                                                                                                    
     NEED                  2       11.76                                                                                                                                    
     MOVE                  1        5.88                                                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
     DEALERTYPE    Frequency     Percent                                                                                                                                    
     -----------------------------------                                                                                                                                    
     A1                   8       47.06                                                                                                                                     
     C1                   6       35.29                                                                                                                                     
     B1                   2       11.76                                                                                                                                     
     A2                   1        5.88                                                                                                                                     
                                                                                                                                                                            
                                                                                                                                                                            
     PROVINCE    Frequency     Percent                                                                                                                                      
     ---------------------------------                                                                                                                                      
     BC                 5       29.41                                                                                                                                       
     ON                 5       29.41                                                                                                                                       
     QC                 3       17.65                                                                                                                                       
     AB                 2       11.76                                                                                                                                       
     NS                 2       11.76                                                                                                                                       
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
     5 most frequent values of GOODCREDIT    ( )                                                                                                                            
                                                                                                                                                                            
     2 distinct values in total                                                                                                                                             
                                                                                                                                                                            
     Rank     Value        Frequency                                                                                                                                        
     ----     -----        ---------                                                                                                                                        
                                                                                                                                                                            
                                                                                                                                                                            
       1    1                    10                                                                                                                                         
       2    0                     7                                                                                                                                         
                                                                                                                                                                            
                                                                                                                                                                            
    5 most frequent values of RATEPLAN      ( )                                                                                                                             
                                                                                                                                                                            
                     2 distinct values in total                                                                                                                             
                                                                                                                                                                            
    Rank     Value      Frequency                                                                                                                                           
    ----     -----      ---------                                                                                                                                           
                                                                                                                                                                            
                                                                                                                                                                            
      1    1                  15                                                                                                                                            
      2    2                   2                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    5 most frequent values of AGE           ( )                                                                                                                             
                                                                                                                                                                            
                    17 distinct values in total                                                                                                                             
                                                                                                                                                                            
    Rank     Value                  Frequency                                                                                                                               
    ----     -----                  ---------                                                                                                                               
                                                                                                                                                                            
                                                                                                                                                                            
      1    .                               1   **                                                                                                                           
      2    26                              1                                                                                                                                
      3    41                              1                                                                                                                                
      4    42                              1                                                                                                                                
      5    45                              1                                                                                                                                
                                                                                                                                                                            
                                                                                                                                                                            
    5  least frequent values                                                                                                                                                
                                                                                                                                                                            
     12    68                              1                                                                                                                                
     13    73                              1                                                                                                                                
     14    75                              1                                                                                                                                
     15    77                              1                                                                                                                                
     16    82                              1                                                                                                                                
     17    92                              1                                                                                                                                
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    5 most frequent values of SALES         ( )                                                                                                                             
                                                                                                                                                                            
                    14 distinct values in total                                                                                                                             
                                                                                                                                                                            
    Rank     Value                Frequency                                                                                                                                 
    ----     -----                ---------                                                                                                                                 
                                                                                                                                                                            
                                                                                                                                                                            
      1    .                             2                                                                                                                                  
      2    $72                           2                                                                                                                                  
      3    $83                           2                                                                                                                                  
      4    $11                           1                                                                                                                                  
      5    $16                           1                                                                                                                                  
                                                                                                                                                                            
                                                                                                                                                                            
    5  least frequent values                                                                                                                                                
                                                                                                                                                                            
      9    $154                          1                                                                                                                                  
     10    $179                          1                                                                                                                                  
     11    $529                          1                                                                                                                                  
     12    $593                          1                                                                                                                                  
     13    $705                          1                                                                                                                                  
     14    $1,041                        1                                                                                                                                  
                                                                                                                                                                            
                                                                                                                                                                            
    The MEANS Procedure                                                                                                                                                     
                                                                                                                                                                            
                           N                                                                                                                                                
    Variable       N    Miss         Minimum         Maximum            Mean          Median         Std Dev             Sum                                                
    ------------------------------------------------------------------------------------------------------------------------                                                
    ACTDT         17       0        14360.00        14957.00        14675.47        14683.00     183.9232577       249483.00                                                
    AGE           16       1      26.0000000      92.0000000      58.8125000      56.0000000      17.6152160     941.0000000                                                
    DEACTDT        3      14        14532.00        14990.00        14797.67        14871.00     237.6432901        44393.00                                                
    GOODCREDIT    17       0               0       1.0000000       0.5882353       1.0000000       0.5072997      10.0000000                                                
    RATEPLAN      17       0       1.0000000       2.0000000       1.1176471       1.0000000       0.3321056      19.0000000                                                
    SALES         15       2      11.0000000         1041.00     256.2666667     128.0000000     309.7998125         3844.00                                                
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
       Univariate distribution of ACTDT (   ) values                                                                                                                        
        Distinct values: 16                                                                                                                                                 
        Format in dataset:  MMDDYY10.                                                                                                                                       
        -----------------------------------------------------------------                                                                                                   
                                                                                                                                                                            
        n            17                              min       04/26/1999                                                                                                   
        nmiss         0                              P1        04/26/1999                                                                                                   
                                                     P5        04/26/1999                                                                                                   
        mean                 03/06/2000              P10       06/20/1999                                                                                                   
        std - days                  183.92           Q1        10/19/1999                                                                                                   
        std - years                   0.50           median    03/14/2000                                                                                                   
                                                     Q3        07/01/2000                                                                                                   
        range - days                597              P90       11/28/2000                                                                                                   
        range - years                 1.64           P95       12/13/2000                                                                                                   
                                                     P99       12/13/2000                                                                                                   
        Q1-Q3 - days                256              max       12/13/2000                                                                                                   
                                                                                                                                                                            
                                                                                                                                                                            
        Q1-Q3 - years                 0.70                                                                                                                                  
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
        Univariate distribution of DEACTDT (   ) values                                                                                                                     
        Distinct values: 3                                                                                                                                                  
        Format in dataset:  MMDDYY10.                                                                                                                                       
        -----------------------------------------------------------------                                                                                                   
                                                                                                                                                                            
        n             3                              min       10/15/1999                                                                                                   
        nmiss        14                              P1        10/15/1999                                                                                                   
                                                     P5        10/15/1999                                                                                                   
        mean                 07/06/2000              P10       10/15/1999                                                                                                   
        std - days                  237.64           Q1        10/15/1999                                                                                                   
        std - years                   0.65           median    09/18/2000                                                                                                   
                                                     Q3        01/15/2001                                                                                                   
        range - days                458              P90       01/15/2001                                                                                                   
        range - years                 1.25           P95       01/15/2001                                                                                                   
                                                     P99       01/15/2001                                                                                                   
        Q1-Q3 - days                458              max       01/15/2001                                                                                                   
        Q1-Q3 - years                 1.25                                                                                                                                  
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    DATA VERIFICATION + VALIDATION FOR WORK.HAVE                                                                                                                            
    have                                                                                                                                                                    
    Univariate tabulations non-date/time/datetime Numeric variables                                                                                                         
    includes only variables with TWO or more values                                                                                                                         
                                                                                                                                                                            
    The UNIVARIATE Procedure                                                                                                                                                
    Variable:  AGE                                                                                                                                                          
                                                                                                                                                                            
    Quantiles (Definition 5)                                                                                                                                                
                                                                                                                                                                            
    Level         Quantile                                                                                                                                                  
                                                                                                                                                                            
    100% Max            92                                                                                                                                                  
    99%                 92                                                                                                                                                  
    95%                 92                                                                                                                                                  
    90%                 82                                                                                                                                                  
    75% Q3              74                                                                                                                                                  
    50% Median          56                                                                                                                                                  
    25% Q1              46                                                                                                                                                  
    10%                 41                                                                                                                                                  
    5%                  26                                                                                                                                                  
    1%                  26                                                                                                                                                  
    0% Min              26                                                                                                                                                  
                                                                                                                                                                            
            Extreme Observations                                                                                                                                            
                                                                                                                                                                            
    ----Lowest----        ----Highest---                                                                                                                                    
                                                                                                                                                                            
    Value      Obs        Value      Obs                                                                                                                                    
                                                                                                                                                                            
       26       11           73       12                                                                                                                                    
       41       14           75        9                                                                                                                                    
       42       10           77        7                                                                                                                                    
       45        2           82        5                                                                                                                                    
       47        4           92        6                                                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
                   Missing Values                                                                                                                                           
                                                                                                                                                                            
                           -----Percent Of-----                                                                                                                             
    Missing                             Missing                                                                                                                             
      Value       Count     All Obs         Obs                                                                                                                             
                                                                                                                                                                            
          .           1        5.88      100.00                                                                                                                             
                                                                                                                                                                            
                                                                                                                                                                            
       Stem Leaf                     #  Boxplot                        Normal Probability Plot                                                                              
          9 2                        1     |          95+                                           *+++++                                                                  
          8 2                        1     |            |                                      *++++                                                                        
          7 357                      3  +-----+         |                               *+*+*++                                                                             
          6 8                        1  |     |         |                          +++*++                                                                                   
          5 03578                    5  *--+--*         |                    +*+**+**                                                                                       
          4 1257                     4  +-----+         |            *  *+*+*                                                                                               
          3                                |            |         ++++++                                                                                                    
          2 6                        1     |          25+   ++++*+                                                                                                          
            ----+----+----+----+                         +----+----+----+----+----+----+----+----+----+----+                                                                
        Multiply Stem.Leaf by 10**+1                         -2        -1         0        +1        +2                                                                     
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    DATA VERIFICATION + VALIDATION FOR WORK.HAVE                                                                                                                            
    have                                                                                                                                                                    
    Univariate tabulations non-date/time/datetime Numeric variables                                                                                                         
    includes only variables with TWO or more values                                                                                                                         
                                                                                                                                                                            
    The UNIVARIATE Procedure                                                                                                                                                
    Variable:  GOODCREDIT                                                                                                                                                   
                                                                                                                                                                            
    Quantiles (Definition 5)                                                                                                                                                
                                                                                                                                                                            
    Level         Quantile                                                                                                                                                  
                                                                                                                                                                            
    100% Max             1                                                                                                                                                  
    99%                  1                                                                                                                                                  
    95%                  1                                                                                                                                                  
    90%                  1                                                                                                                                                  
    75% Q3               1                                                                                                                                                  
    50% Median           1                                                                                                                                                  
    25% Q1               0                                                                                                                                                  
    10%                  0                                                                                                                                                  
    5%                   0                                                                                                                                                  
    1%                   0                                                                                                                                                  
    0% Min               0                                                                                                                                                  
                                                                                                                                                                            
            Extreme Observations                                                                                                                                            
                                                                                                                                                                            
    ----Lowest----        ----Highest---                                                                                                                                    
                                                                                                                                                                            
    Value      Obs        Value      Obs                                                                                                                                    
                                                                                                                                                                            
        0       17            1        8                                                                                                                                    
        0       16            1       10                                                                                                                                    
        0       14            1       11                                                                                                                                    
        0       13            1       12                                                                                                                                    
        0        9            1       15                                                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
       Stem Leaf                     #  Boxplot                        Normal Probability Plot                                                                              
         10 0000000000              10  +-----+      1.1+                        *** * ** *+*++*    *                                                                       
          8                             |     |         |                              ++++                                                                                 
          6                             |     |         |                          ++++                                                                                     
          4                             |  +  |         |                      ++++                                                                                         
          2                             |     |         |                  ++++                                                                                             
          0 0000000                  7  +-----+      0.1+       *    * +*+* ** *                                                                                            
            ----+----+----+----+                         +----+----+----+----+----+----+----+----+----+----+                                                                
        Multiply Stem.Leaf by 10**-1                         -2        -1         0        +1        +2                                                                     
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    DATA VERIFICATION + VALIDATION FOR WORK.HAVE                                                                                                                            
    have                                                                                                                                                                    
    Univariate tabulations non-date/time/datetime Numeric variables                                                                                                         
    includes only variables with TWO or more values                                                                                                                         
                                                                                                                                                                            
    The UNIVARIATE Procedure                                                                                                                                                
    Variable:  RATEPLAN                                                                                                                                                     
                                                                                                                                                                            
                                                                                                                                                                            
    Quantiles (Definition 5)                                                                                                                                                
                                                                                                                                                                            
    Level         Quantile                                                                                                                                                  
                                                                                                                                                                            
    100% Max             2                                                                                                                                                  
    99%                  2                                                                                                                                                  
    95%                  2                                                                                                                                                  
    90%                  2                                                                                                                                                  
    75% Q3               1                                                                                                                                                  
    50% Median           1                                                                                                                                                  
    25% Q1               1                                                                                                                                                  
    10%                  1                                                                                                                                                  
    5%                   1                                                                                                                                                  
    1%                   1                                                                                                                                                  
    0% Min               1                                                                                                                                                  
                                                                                                                                                                            
            Extreme Observations                                                                                                                                            
                                                                                                                                                                            
    ----Lowest----        ----Highest---                                                                                                                                    
                                                                                                                                                                            
    Value      Obs        Value      Obs                                                                                                                                    
                                                                                                                                                                            
        1       17            1       15                                                                                                                                    
        1       16            1       16                                                                                                                                    
        1       15            1       17                                                                                                                                    
        1       14            2        4                                                                                                                                    
        1       13            2       10                                                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
       Stem Leaf                     #  Boxplot                        Normal Probability Plot                                                                              
         20 00                       2     *         2.1+                                      *    *                                                                       
         18                                             |                                              +++++                                                                
         16                                             |                                        ++++++                                                                     
         14                                             |                                  ++++++                                                                           
         12                                             |                            ++++++                                                                                 
         10 000000000000000         15  +--+--+      1.1+       *    *  * * ** *+***+* ** * *                                                                               
            ----+----+----+----+                         +----+----+----+----+----+----+----+----+----+----+                                                                
        Multiply Stem.Leaf by 10**-1                         -2        -1         0        +1        +2                                                                     
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    DATA VERIFICATION + VALIDATION FOR WORK.HAVE                                                                                                                            
    have                                                                                                                                                                    
    Univariate tabulations non-date/time/datetime Numeric variables                                                                                                         
    includes only variables with TWO or more values                                                                                                                         
                                                                                                                                                                            
    The UNIVARIATE Procedure                                                                                                                                                
    Variable:  SALES                                                                                                                                                        
                                                                                                                                                                            
    Quantiles (Definition 5)                                                                                                                                                
                                                                                                                                                                            
    Level         Quantile                                                                                                                                                  
                                                                                                                                                                            
    100% Max          1041                                                                                                                                                  
    99%               1041                                                                                                                                                  
    95%               1041                                                                                                                                                  
    90%                705                                                                                                                                                  
    75% Q3             529                                                                                                                                                  
    50% Median         128                                                                                                                                                  
    25% Q1              72                                                                                                                                                  
    10%                 16                                                                                                                                                  
    5%                  11                                                                                                                                                  
    1%                  11                                                                                                                                                  
    0% Min              11                                                                                                                                                  
                                                                                                                                                                            
            Extreme Observations                                                                                                                                            
                                                                                                                                                                            
    ----Lowest----        ----Highest---                                                                                                                                    
                                                                                                                                                                            
    Value      Obs        Value      Obs                                                                                                                                    
                                                                                                                                                                            
       11       10          179       13                                                                                                                                    
       16       12          529       16                                                                                                                                    
       44       17          593        3                                                                                                                                    
       72        8          705       14                                                                                                                                    
       72        2         1041        6                                                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
                   Missing Values                                                                                                                                           
                                                                                                                                                                            
                           -----Percent Of-----                                                                                                                             
    Missing                             Missing                                                                                                                             
      Value       Count     All Obs         Obs                                                                                                                             
                                                                                                                                                                            
          .           2       11.76      100.00                                                                                                                             
                                                                                                                                                                            
                                                                                                                                                                            
       Stem Leaf                     #  Boxplot                        Normal Probability Plot                                                                              
         10 4                        1     |        1100+                                          *       +                                                                
          8                                |            |                                           +++++++                                                                 
          6 0                        1     |            |                                     *+++++                                                                        
          4 39                       2  +-----+         |                              ++*+*++                                                                              
          2                             |  +  |         |                        ++++++                                                                                     
          0 12477883358             11  *-----*      100+        *    *  *+*+*+** * ** *                                                                                    
            ----+----+----+----+                         +----+----+----+----+----+----+----+----+----+----+                                                                
        Multiply Stem.Leaf by 10**+2                                                                                                                                        
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Maximums and Minimums work.have                                                                                                                                         
                                                                                                                                                                            
    VARIABLE       MIN              MAX                                                                                                                                     
                                                                                                                                                                            
    ACCTNO         1176913194483    1177066422248                                                                                                                           
    DEACTREASON    MOVE             NEED                                                                                                                                    
    DEALERTYPE     A1               C1                                                                                                                                      
    PROVINCE       AB               QC                                                                                                                                      
    ACTDT          14360            14957                                                                                                                                   
    DEACTDT        14532            14990                                                                                                                                   
    SALES          11               1041                                                                                                                                    
    GOODCREDIT     0                1                                                                                                                                       
    RATEPLAN       1                2                                                                                                                                       
    AGE            26               92                                                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Variable Name Aliases for work.have for Use in Mising Value Pattern Analysis                                                                                            
    Missing data patterns: sorted by descending percent                                                                                                                     
                                                                                                                                                                            
    Obs    FREQ    PERCENT    GROUP    ACCTNO    DEACTREASON    DEALERTYPE    PROVINCE    ACTDT    DEACTDT    SALES    GOODCREDIT    RATEPLAN    AGE    MISSING             
                                                                                                                                                                            
     1      11      64.7        2        X            .             X            X          X         .         X          X            X         X        2                
     2       3      17.6        1        X            X             X            X          X         X         X          X            X         X        0                
     3       2      11.8        4        X            .             X            X          X         .         .          X            X         X        3                
     4       1       5.9        3        X            .             X            X          X         .         X          X            X         .        3                
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Maximum Number of Bytes to hold Character and Numeric Vales Exactly                                                                                                     
                                                                                                                                                                            
                    VARIABLE_                    NEW_                                                                                                                       
    Obs    __TYP      TYPE       NAME           LENGTH    ORIGINAL    SAVINGS                                                                                               
                                                                                                                                                                            
      1      C      Character    ACCTNO           13         13          0                                                                                                  
      2      C      Character    DEACTREASON       4          4          0                                                                                                  
      3      C      Character    DEALERTYPE        2          2          0                                                                                                  
      4      C      Character    PROVINCE          2          2          0                                                                                                  
      5      N      Numeric      ACTDT             4          8          4                                                                                                  
      6      N      Numeric      AGE               3          8          5                                                                                                  
      7      N      Numeric      DEACTDT           4          8          4                                                                                                  
      8      N      Numeric      GOODCREDIT        3          8          5                                                                                                  
      9      N      Numeric      RATEPLAN          3          8          5                                                                                                  
     10      N      Numeric      SALES             3          8          5                                                                                                  
                                                                                                                                                                            
                                                                                                                                                                            
    ******************************************************************                                                                                                      
    *                                                                *                                                                                                      
    * No duplicates in acctno in work have                                                                                                                                  
    *                                                                *                                                                                                      
    ******************************************************************                                                                                                      
    Histogram for numeric variable ACTDT                                                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
         ACTDT                                                                                            Cum.              Cum.                                            
        Midpoint                                                                                    Freq  Freq  Percent  Percent                                            
    06/05/1999   |****************************************                                             2     2    11.76    11.76                                            
    08/24/1999   |********************                                                                 1     3     5.88    17.65                                            
    11/12/1999   |********************************************************************************     4     7    23.53    41.18                                            
    01/31/2000   |********************                                                                 1     8     5.88    47.06                                            
    04/20/2000   |****************************************                                             2    10    11.76    58.82                                            
    07/09/2000   |************************************************************                         3    13    17.65    76.47                                            
    09/27/2000   |****************************************                                             2    15    11.76    88.24                                            
    12/16/2000   |****************************************                                             2    17    11.76   100.00                                            
                 --------------------+-------------------+-------------------+-------------------+                                                                          
                                     1                   2                   3                   4                                                                          
                                                     Frequency                                                                                                              
                                                                                                                                                                            
    AGE                                                                                                                                    Cum.              Cum.           
    Midpoint                                                                                                                         Freq  Freq  Percent  Percent           
     25   |****************************************                                                                                     1     1     6.25     6.25           
     40   |********************************************************************************                                             2     3    12.50    18.75           
     45   |********************************************************************************                                             2     5    12.50    31.25           
     50   |****************************************                                                                                     1     6     6.25    37.50           
     55   |************************************************************************************************************************     3     9    18.75    56.25           
     60   |****************************************                                                                                     1    10     6.25    62.50           
     70   |****************************************                                                                                     1    11     6.25    68.75           
     75   |************************************************************************************************************************     3    14    18.75    87.50           
     80   |****************************************                                                                                     1    15     6.25    93.75           
     90   |****************************************                                                                                     1    16     6.25   100.00           
          ----------------------------------------+---------------------------------------+---------------------------------------+                                         
                                                  1                                       2                                       3                                         
                                                                                                                                                                            
                                                                                                                                                                            
    Histogram for character variable DEACTREASON                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    SIXTEE                                                    Cum.              Cum.                                                                                        
                                                        Freq  Freq  Percent  Percent                                                                                        
             |                                                                                                                                                              
    NEED     |****************************************     2     2    66.67    66.67                                                                                        
             |                                                                                                                                                              
    MOVE     |********************                         1     3    33.33   100.00                                                                                        
             |                                                                                                                                                              
             --------------------+-------------------+                                                                                                                      
                                 1                   2                                                                                                                      
                                                                                                                                                                            
                             Frequency                                                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Histogram for character variable DEALERTYPE                                                                                                                             
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    SIXTEE                                                    Cum.              Cum.                                                                                        
                                                        Freq  Freq  Percent  Percent                                                                                        
             |                                                                                                                                                              
    A1       |****************************************     8     8    47.06    47.06                                                                                        
             |                                                                                                                                                              
    C1       |******************************               6    14    35.29    82.35                                                                                        
             |                                                                                                                                                              
    B1       |**********                                   2    16    11.76    94.12                                                                                        
             |                                                                                                                                                              
    A2       |*****                                        1    17     5.88   100.00                                                                                        
             |                                                                                                                                                              
             -----+----+----+----+----+----+----+----+                                                                                                                      
                  1    2    3    4    5    6    7    8                                                                                                                      
                                                                                                                                                                            
                             Frequency                                                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    GOODCREDIT                                                                                                                Cum.              Cum.                        
     Midpoint                                                                                                           Freq  Freq  Percent  Percent                        
           0.0   |**********************************************************************                                   7     7    41.18    41.18                        
           1.0   |****************************************************************************************************    10    17    58.82   100.00                        
                 ----------+---------+---------+---------+---------+---------+---------+---------+---------+---------+                                                      
                           1         2         3         4         5         6         7         8         9         10                                                     
                                                               Frequency                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Histogram for character variable PROVINCE                                                                                                                               
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    SIXTEE                                                              Cum.              Cum.                                                                              
                                                                  Freq  Freq  Percent  Percent                                                                              
             |                                                                                                                                                              
    ON       |**************************************************     5     5    29.41    29.41                                                                              
             |                                                                                                                                                              
    BC       |**************************************************     5    10    29.41    58.82                                                                              
             |                                                                                                                                                              
    QC       |******************************                         3    13    17.65    76.47                                                                              
             |                                                                                                                                                              
    NS       |********************                                   2    15    11.76    88.24                                                                              
             |                                                                                                                                                              
    AB       |********************                                   2    17    11.76   100.00                                                                              
             |                                                                                                                                                              
             ----------+---------+---------+---------+---------+                                                                                                            
                       1         2         3         4         5                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    istogram for numeric variable RATEPLAN                                                                                                                                  
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    RATEPLAN                                                                                       Cum.              Cum.                                                   
    Midpoint                                                                                 Freq  Freq  Percent  Percent                                                   
         1.0   |***************************************************************************    15    15    88.24    88.24                                                   
         2.0   |**********                                                                      2    17    11.76   100.00                                                   
               -----+----+----+----+----+----+----+----+----+----+----+----+----+----+----+                                                                                 
                    1    2    3    4    5    6    7    8    9    10   11   12   13   14   15                                                                                
                                                 Frequency                                                                                                                  
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Histogram for numeric variable SALES                                                                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
     SALES                                                                                                                                    Cum.              Cum.        
    Midpoint                                                                                                                            Freq  Freq  Percent  Percent        
        $0   |************************************************************                                                                 3     3    20.00    20.00        
      $100   |************************************************************************************************************************     6     9    40.00    60.00        
      $200   |****************************************                                                                                     2    11    13.33    73.33        
      $500   |********************                                                                                                         1    12     6.67    80.00        
      $600   |********************                                                                                                         1    13     6.67    86.67        
      $700   |********************                                                                                                         1    14     6.67    93.33        
    $1,000   |********************                                                                                                         1    15     6.67   100.00        
             --------------------+-------------------+-------------------+-------------------+-------------------+-------------------+                                      
                                 1                   2                   3                   4                   5                   6                                      
                                                                     Frequency                                                                                              
                                                                                                                                                                            
                                                                                                                                                                            
    Missing vs Populated Frequencies                                                                                                                                        
                                                                                                                                                                            
                    Populated,  Missing and Missing Frequencies and Percents                                                                                                
                                                                                Missing#Pe                                                                                  
      Variable                                   Populated             Missing       rcent                                                                                  
      ACCTNO                                            17                   0      0.00%                                                                                   
      DEACTREASON                                        3                  14     82.35%                                                                                   
      DEALERTYPE                                        17                   0      0.00%                                                                                   
      PROVINCE                                          17                   0      0.00%                                                                                   
      ACTDT                                             17                   0      0.00%                                                                                   
      DEACTDT                                            3                  14     82.35%                                                                                   
      SALES                                             15                   2     11.76%                                                                                   
      GOODCREDIT                                        17                   0      0.00%                                                                                   
      RATEPLAN                                          17                   0      0.00%                                                                                   
      AGE                                               16                   1      5.88%                                                                                   
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Missing vs Populated Frequencies                                                                                                                                        
                                                                                                                                                                            
    The FREQ Procedure                                                                                                                                                      
                                                                                                                                                                            
                                          Cumulative    Cumulative                                                                                                          
    ACCTNO       Frequency     Percent     Frequency      Percent                                                                                                           
    --------------------------------------------------------------                                                                                                          
    Populated          17      100.00            17       100.00                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                            Cumulative    Cumulative                                                                                                        
    DEACTREASON    Frequency     Percent     Frequency      Percent                                                                                                         
    ----------------------------------------------------------------                                                                                                        
    Missing              14       82.35            14        82.35                                                                                                          
    Populated             3       17.65            17       100.00                                                                                                          
                                                                                                                                                                            
                                                                                                                                                                            
                                           Cumulative    Cumulative                                                                                                         
    DEALERTYPE    Frequency     Percent     Frequency      Percent                                                                                                          
    ---------------------------------------------------------------                                                                                                         
    Populated           17      100.00            17       100.00                                                                                                           
                                                                                                                                                                            
                                                                                                                                                                            
                                          Cumulative    Cumulative                                                                                                          
    PROVINCE     Frequency     Percent     Frequency      Percent                                                                                                           
    --------------------------------------------------------------                                                                                                          
    Populated          17      100.00            17       100.00                                                                                                            
                                                                                                                                                                            
    Missing vs Populated Frequencies                                                                                                                                        
                                                                                                                                                                            
    The FREQ Procedure                                                                                                                                                      
                                                                                                                                                                            
                                                Cumulative    Cumulative                                                                                                    
              ACTDT    Frequency     Percent     Frequency      Percent                                                                                                     
    --------------------------------------------------------------------                                                                                                    
    Positive                 17      100.00            17       100.00                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
                                                Cumulative    Cumulative                                                                                                    
            DEACTDT    Frequency     Percent     Frequency      Percent                                                                                                     
    --------------------------------------------------------------------                                                                                                    
    Missing                  14       82.35            14        82.35                                                                                                      
    Positive                  3       17.65            17       100.00                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
                                                Cumulative    Cumulative                                                                                                    
              SALES    Frequency     Percent     Frequency      Percent                                                                                                     
    --------------------------------------------------------------------                                                                                                    
    Missing                   2       11.76             2        11.76                                                                                                      
    Positive                 15       88.24            17       100.00                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
                                                Cumulative    Cumulative                                                                                                    
         GOODCREDIT    Frequency     Percent     Frequency      Percent                                                                                                     
    --------------------------------------------------------------------                                                                                                    
    Zero                      7       41.18             7        41.18                                                                                                      
    Positive                 10       58.82            17       100.00                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
                                                Cumulative    Cumulative                                                                                                    
           RATEPLAN    Frequency     Percent     Frequency      Percent                                                                                                     
    --------------------------------------------------------------------                                                                                                    
    Positive                 17      100.00            17       100.00                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
                                                Cumulative    Cumulative                                                                                                    
                AGE    Frequency     Percent     Frequency      Percent                                                                                                     
    --------------------------------------------------------------------                                                                                                    
    Missing                   1        5.88             1         5.88                                                                                                      
    Positive                 16       94.12            17       100.00                                                                                                      
                                                                                                                                                                            
                                                                                                                                                                            
    Variable Correlations (Spearman)                                                                                                                                        
                                                                                                                                                                            
                  Correlated    Correlation    Number    Spearman                                                                                                           
    Variable         With           Coef       of Obs       P                                                                                                               
                                                                                                                                                                            
    DEACTDT       ACTDT           1.00000         3       <.0001                                                                                                            
    GOODCREDIT    DEACTDT         0.86603         3       0.1052                                                                                                            
    SALES         DEACTDT         0.50000         3       0.8811                                                                                                            
    AGE           DEACTDT         0.50000         3       0.3618                                                                                                            
    GOODCREDIT    SALES           0.43379        15       0.1052                                                                                                            
    RATEPLAN      SALES           0.38652        15       0.4463                                                                                                            
    AGE           RATEPLAN        0.36896        16       0.3618                                                                                                            
    RATEPLAN      GOODCREDIT      0.30551        17       0.4463                                                                                                            
    SALES         ACTDT           0.24172        15       0.8811                                                                                                            
    AGE           ACTDT           0.08824        16       0.3618                                                                                                            
    AGE           GOODCREDIT      0.08402        16       0.3618                                                                                                            
    AGE           SALES           0.05286        14       0.3618                                                                                                            
    GOODCREDIT    ACTDT           0.02441        17       0.1052                                                                                                            
    RATEPLAN      ACTDT           0.00000        17       0.4463                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Obs                       OUT                                                                                                                                           
                                                                                                                                                                            
      1    One to Many     ACTDT to AGE                                                                                                                                     
      2    Many to One     ACTDT to DEACTDT                                                                                                                                 
      3    Many to One     ACTDT to GOODCREDIT                                                                                                                              
      4    Many to One     ACTDT to RATEPLAN                                                                                                                                
      5    Many to Many    ACTDT to SALES                                                                                                                                   
      6    Many to One     ACTDT to DEACTREASON                                                                                                                             
      7    Many to One     ACTDT to DEALERTYPE                                                                                                                              
      8    Many to Many    ACTDT to PROVINCE                                                                                                                                
      9    One to Many     ACTDT to ACCTNO                                                                                                                                  
     10    Many to One     AGE to DEACTDT                                                                                                                                   
     11    Many to One     AGE to GOODCREDIT                                                                                                                                
     12    Many to One     AGE to RATEPLAN                                                                                                                                  
     13    Many to One     AGE to SALES                                                                                                                                     
     14    Many to One     AGE to DEACTREASON                                                                                                                               
     15    Many to One     AGE to DEALERTYPE                                                                                                                                
     16    Many to One     AGE to PROVINCE                                                                                                                                  
     17    One to One      AGE to ACCTNO                                                                                                                                    
     18    Many to Many    DEACTDT to GOODCREDIT                                                                                                                            
     19    Many to Many    DEACTDT to RATEPLAN                                                                                                                              
     20    Many to Many    DEACTDT to SALES                                                                                                                                 
     21    Many to One     DEACTDT to DEACTREASON                                                                                                                           
     22    Many to Many    DEACTDT to DEALERTYPE                                                                                                                            
     23    Many to Many    DEACTDT to PROVINCE                                                                                                                              
     24    One to Many     DEACTDT to ACCTNO                                                                                                                                
     25    Many to Many    GOODCREDIT to RATEPLAN                                                                                                                           
     26    One to Many     GOODCREDIT to SALES                                                                                                                              
     27    Many to Many    GOODCREDIT to DEACTREASON                                                                                                                        
     28    Many to Many    GOODCREDIT to DEALERTYPE                                                                                                                         
     29    Many to Many    GOODCREDIT to PROVINCE                                                                                                                           
     30    One to Many     GOODCREDIT to ACCTNO                                                                                                                             
     31    Many to Many    RATEPLAN to SALES                                                                                                                                
     32    Many to Many    RATEPLAN to DEACTREASON                                                                                                                          
     33    Many to Many    RATEPLAN to DEALERTYPE                                                                                                                           
     34    Many to Many    RATEPLAN to PROVINCE                                                                                                                             
     35    One to Many     RATEPLAN to ACCTNO                                                                                                                               
     36    Many to Many    SALES to DEACTREASON                                                                                                                             
     37    Many to Many    SALES to DEALERTYPE                                                                                                                              
     38    Many to Many    SALES to PROVINCE                                                                                                                                
     39    One to Many     SALES to ACCTNO                                                                                                                                  
     40    Many to Many    DEACTREASON to DEALERTYPE                                                                                                                        
     41    Many to Many    DEACTREASON to PROVINCE                                                                                                                          
     42    One to Many     DEACTREASON to ACCTNO                                                                                                                            
     43    Many to Many    DEALERTYPE to PROVINCE                                                                                                                           
     44    One to Many     DEALERTYPE to ACCTNO                                                                                                                             
     45    One to Many     PROVINCE to ACCTNO                                                                                                                               
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    Cramer V                                                                                                                                                                
    ALL PAIRS OF VARIABLES WHERE MAX LEVELS IS 2000 AND MAX NUMBER OF VARIABLES IS 30                                                                                       
    ACCTNO *                                                                                                                                                                
                                                                                                                                                                            
    Obs    TABLE                             STATISTIC     VALUE                                                                                                            
                                                                                                                                                                            
      1    Table AGE * SALES                 Cramer's V    1.0000                                                                                                           
      2    Table ACTDT * AGE                 Cramer's V    1.0000                                                                                                           
      3    Table ACTDT * ACCTNO              Cramer's V    1.0000                                                                                                           
      4    Table SALES * ACCTNO              Cramer's V    1.0000                                                                                                           
      5    Table AGE * ACCTNO                Cramer's V    1.0000                                                                                                           
      6    Table ACTDT * DEACTDT             Cramer's V    1.0000                                                                                                           
      7    Table DEACTDT * ACCTNO            Cramer's V    1.0000                                                                                                           
      8    Table AGE * DEACTDT               Cramer's V    1.0000                                                                                                           
      9    Table ACTDT * DEACTREASON         Cramer's V    1.0000                                                                                                           
     10    Table AGE * PROVINCE              Cramer's V    1.0000                                                                                                           
     11    Table GOODCREDIT * SALES          Cramer's V    1.0000                                                                                                           
     12    Table GOODCREDIT * ACCTNO         Cramer's V    1.0000                                                                                                           
     13    Table PROVINCE * ACCTNO           Cramer's V    1.0000                                                                                                           
     14    Table ACTDT * GOODCREDIT          Cramer's V    1.0000                                                                                                           
     15    Table AGE * GOODCREDIT            Cramer's V    1.0000                                                                                                           
     16    Table AGE * DEACTREASON           Cramer's V    1.0000                                                                                                           
     17    Table DEACTDT * DEACTREASON       Cramer's V    1.0000                                                                                                           
     18    Table ACTDT * RATEPLAN            Cramer's V    1.0000                                                                                                           
     19    Table AGE * RATEPLAN              Cramer's V    1.0000                                                                                                           
     20    Table AGE * DEALERTYPE            Cramer's V    1.0000                                                                                                           
     21    Table ACTDT * DEALERTYPE          Cramer's V    1.0000                                                                                                           
     22    Table RATEPLAN * ACCTNO           Cramer's V    1.0000                                                                                                           
     23    Table DEACTREASON * ACCTNO        Cramer's V    1.0000                                                                                                           
     24    Table DEALERTYPE * ACCTNO         Cramer's V    1.0000                                                                                                           
                                                                                                                                                                            
                                                                                                                                                                            
                                                                                                                                                                            
    The CONTENTS Procedure                                                                                                                                                  
                                                                                                                                                                            
                    Variables in Creation Order                                                                                                                             
                                                                                                                                                                            
     #    Variable       Type    Len    Format       Informat                                                                                                               
                                                                                                                                                                            
     1    ACCTNO         Char     13                                                                                                                                        
     2    DEACTREASON    Char      4                                                                                                                                        
     3    DEALERTYPE     Char      2                                                                                                                                        
     4    PROVINCE       Char      2                                                                                                                                        
     5    ACTDT          Num       8    MMDDYY10.    MMDDYY10.                                                                                                              
     6    DEACTDT        Num       8    MMDDYY10.    MMDDYY10.                                                                                                              
     7    SALES          Num       8    DOLLAR8.     DOLLAR8.                                                                                                               
     8    GOODCREDIT     Num       8                                                                                                                                        
     9    RATEPLAN       Num       8                                                                                                                                        
    10    AGE            Num       8                                                                                                                                        
   
