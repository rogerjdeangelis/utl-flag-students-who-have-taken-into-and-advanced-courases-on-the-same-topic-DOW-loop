# utl-flag-students-who-have-taken-into-and-advanced-courases-on-the-same-topic-DOW-loop
Flag students who have taken into and advanced courases on the same topic DOW loop 
    Flag students who have taken intro and advanced courses on the same topic DOW loop                                                
                                                                                                                                      
    What I am trying to do is to flag the student who transition from l                                                               
    ower course sequence to higher course sequence for the same course.                                                               
                                                                                                                                      
    ie Algegra 1                                                                                                                      
       Algebra 2                                                                                                                      
                                                                                                                                      
    github                                                                                                                            
    https://tinyurl.com/yyh7pp3b                                                                                                      
    https://github.com/rogerjdeangelis/utl-flag-students-who-have-taken-intro-and-advanced-courses-on-the-same-topic-DOW-loop         
                                                                                                                                      
    SAS-L                                                                                                                             
    https://listserv.uga.edu/cgi-bin/wa?A2=SAS-L;1eac7863.1906c                                                                       
                                                                                                                                      
    Flag students who have taken into and advanced courases on the same topic DOW loop                                                
                                                                                                                                      
        Two Solutions                                                                                                                 
                                                                                                                                      
            1. Sort then DOW loop                                                                                                     
                                                                                                                                      
            2, Single datastep ( reasonable assumptions about sort order)                                                             
               Solution by                                                                                                            
                 Bartosz Jablonski                                                                                                    
                 yabwon@gmail.com                                                                                                     
                                                                                                                                      
    *_                   _                                                                                                            
    (_)_ __  _ __  _   _| |_                                                                                                          
    | | '_ \| '_ \| | | | __|                                                                                                         
    | | | | | |_) | |_| | |_                                                                                                          
    |_|_| |_| .__/ \__,_|\__|                                                                                                         
            |_|                                                                                                                       
    ;                                                                                                                                 
                                                                                                                                      
    data have;                                                                                                                        
      input COURSE $4. @6 lvl 4. @10 id $8.;                                                                                          
    cards4;                                                                                                                           
    BASL-0101 0000001                                                                                                                 
    BASM-0101 0000001                                                                                                                 
    TRCT-0601 0000001                                                                                                                 
    TRCT-0601 0000003                                                                                                                 
    TRCT-0601 0000004                                                                                                                 
    ESLA-0301 0000002                                                                                                                 
    ESLO-0301 0000002                                                                                                                 
    ESLW-0301 0000002                                                                                                                 
    TRCT-0601 0000005                                                                                                                 
    GEDM-0401 0000006                                                                                                                 
    GEDM-0501 0000006                                                                                                                 
    GEDM-0301 0000007                                                                                                                 
    GEDR-0301 0000007                                                                                                                 
    ESLO-0401 0000008                                                                                                                 
    ESLW-0401 0000008                                                                                                                 
    GEDM-0301 0000009                                                                                                                 
    GEDM-0301 0000010                                                                                                                 
    GEDM-0401 0000010                                                                                                                 
    GEDW-0301 0000010                                                                                                                 
    ;;;;                                                                                                                              
    run;quit;                                                                                                                         
                                                                                                                                      
                                                                                                                                      
    * I am showing the sorted output to document the Rules;                                                                           
                                                                                                                                      
    proc sort data=have out=havSrt;                                                                                                   
    by id  course lvl;                                                                                                                
    run;quit;                                                                                                                         
                                                                                                                                      
                                                                                                                                      
    Up to 40 obs WORK.HAVSRT total obs=19                                                                                             
                                      |  RULES                                                                                        
    Obs    COURSE    LVL      ID      |                                                                                               
                                      |                                                                                               
      1     BASL     101    0000001   |                                                                                               
      2     BASM     101    0000001   |                                                                                               
      3     TRCT     601    0000001   |                                                                                               
                                      |                                                                                               
      4     ESLA     301    0000002   |                                                                                               
      5     ESLO     301    0000002   |                                                                                               
      6     ESLW     301    0000002   |                                                                                               
                                      |                                                                                               
      7     TRCT     601    0000003   |                                                                                               
      8     TRCT     601    0000004   |                                                                                               
      9     TRCT     601    0000005   |                                                                                               
                                      |                                                                                               
     10     GEDM     401    0000006   |  Y                                                                                            
     11     GEDM     501    0000006   |  Y                                                                                            
                                      |                                                                                               
     12     GEDM     301    0000007   |                                                                                               
     13     GEDR     301    0000007   |                                                                                               
                                      |                                                                                               
     14     ESLO     401    0000008   |                                                                                               
     15     ESLW     401    0000008   |                                                                                               
                                      |                                                                                               
     16     GEDM     301    0000009   |                                                                                               
                                      |                                                                                               
     17     GEDM     301    0000010   |  Y                                                                                            
     18     GEDM     401    0000010   |  Y                                                                                            
                                                                                                                                      
     19     GEDW     301    0000010   |                                                                                               
                                                                                                                                      
    *                                                                                                                                 
     _ __  _ __ ___   ___ ___  ___ ___                                                                                                
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                               
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                               
    | .__/|_|  \___/ \___\___||___/___/                                                                                               
    |_|                                                                                                                               
    ;                                                                                                                                 
                                                                                                                                      
    *_                    _                                                                                                           
    / |    ___  ___  _ __| |_                                                                                                         
    | |   / __|/ _ \| '__| __|                                                                                                        
    | |_  \__ \ (_) | |  | |_                                                                                                         
    |_(_) |___/\___/|_|   \__|                                                                                                        
                                                                                                                                      
    ;                                                                                                                                 
                                                                                                                                      
    proc sort data=have out=havSrt;                                                                                                   
    by id  course lvl;                                                                                                                
    run;quit;                                                                                                                         
                                                                                                                                      
                                                                                                                                      
    data want(drop=savLvl);                                                                                                           
                                                                                                                                      
      do _n_ = 1 by 1 until(last.course);                                                                                             
                                                                                                                                      
        set havSrt;                                                                                                                   
        by id course;                                                                                                                 
                                                                                                                                      
        if first.course then savLvl=lvl;                                                                                              
        if last.course and lvl > savLvl then flag='Y';                                                                                
                                                                                                                                      
      end;                                                                                                                            
                                                                                                                                      
      do _n_=1 to _n_;                                                                                                                
                                                                                                                                      
        set havSrt;                                                                                                                   
        output;                                                                                                                       
                                                                                                                                      
      end;                                                                                                                            
                                                                                                                                      
    run;quit;                                                                                                                         
                                                                                                                                      
    NOTE: There were 19 observations read from the data set WORK.HAVSRT.                                                              
    NOTE: There were 19 observations read from the data set WORK.HAVSRT.                                                              
    NOTE: The data set WORK.WANT has 19 observations and 4 variables.                                                                 
                                                                                                                                      
                                                                                                                                      
    Up to 40 obs from WANT total obs=19                                                                                               
                                                                                                                                      
    Obs    COURSE    LVL      ID       FLAG                                                                                           
                                                                                                                                      
      1     BASL     101    0000001                                                                                                   
      2     BASM     101    0000001                                                                                                   
      3     TRCT     601    0000001                                                                                                   
      4     ESLA     301    0000002                                                                                                   
      5     ESLO     301    0000002                                                                                                   
      6     ESLW     301    0000002                                                                                                   
      7     TRCT     601    0000003                                                                                                   
      8     TRCT     601    0000004                                                                                                   
      9     TRCT     601    0000005                                                                                                   
     10     GEDM     401    0000006     Y                                                                                             
     11     GEDM     501    0000006     Y                                                                                             
     12     GEDM     301    0000007                                                                                                   
     13     GEDR     301    0000007                                                                                                   
     14     ESLO     401    0000008                                                                                                   
     15     ESLW     401    0000008                                                                                                   
     16     GEDM     301    0000009                                                                                                   
     17     GEDM     301    0000010     Y                                                                                             
     18     GEDM     401    0000010     Y                                                                                             
     19     GEDW     301    0000010                                                                                                   
                                                                                                                                      
    *____      ____             _                                                                                                     
    |___ \    | __ )  __ _ _ __| |_                                                                                                   
      __) |   |  _ \ / _` | '__| __|                                                                                                  
     / __/ _  | |_) | (_| | |  | |_                                                                                                   
    |_____(_) |____/ \__,_|_|   \__|                                                                                                  
                                                                                                                                      
    ;                                                                                                                                 
                                                                                                                                      
                                                                                                                                      
    From your description I'm assuming that:                                                                                          
    1) data are presorted by student's id and course name (if not, than you will have to do this),                                    
    2) there are two levels of courses (i.e. Low and High)                                                                            
                                                                                                                                      
    With this assumptions it looks like a perfect example for double DoW-loop.                                                        
    Code is below, please let me know if it's what you expected.                                                                      
                                                                                                                                      
    all the best                                                                                                                      
    Bart                                                                                                                              
                                                                                                                                      
    /**/                                                                                                                              
                                                                                                                                      
    data have; /* read in the data */                                                                                                 
    input COURSE_NAME      : $ 20. student_id : $ 10.;                                                                                
    cards;                                                                                                                            
    BASL-0101      0000001                                                                                                            
    BASM-0101      0000001                                                                                                            
    TRCT-0601      0000001                                                                                                            
    TRCT-0601      0000003                                                                                                            
    TRCT-0601      0000004                                                                                                            
    ESLA-0301      0000002                                                                                                            
    ESLO-0301      0000002                                                                                                            
    ESLW-0301      0000002                                                                                                            
    TRCT-0601      0000005                                                                                                            
    GEDM-0401      0000006                                                                                                            
    GEDM-0501      0000006                                                                                                            
    GEDM-0301      0000007                                                                                                            
    GEDR-0301      0000007                                                                                                            
    ESLO-0401      0000008                                                                                                            
    ESLW-0401      0000008                                                                                                            
    GEDM-0301      0000009                                                                                                            
    GEDM-0301      0000010                                                                                                            
    GEDM-0401      0000010                                                                                                            
    GEDW-0301      0000010                                                                                                            
    ;                                                                                                                                 
    run;                                                                                                                              
                                                                                                                                      
    data have_v / view = have_v; /* create view to "split" course_name to course id (e.g. BASL) and course level (clevel) */          
      set;                                                                                                                            
      course = scan(COURSE_NAME, 1, "-");                                                                                             
      clevel = scan(COURSE_NAME, 2, "-");                                                                                             
    run;                                                                                                                              
                                                                                                                                      
    data want;                                                                                                                        
      counter = 0;                                                                                                                    
      do _n_ = 1 by 1 until (last.course); /* loop by view for each student and course id */                                          
        set have_v;                                                                                                                   
        by student_id course clevel notsorted ;                                                                                       
        counter + last.clevel; /* count the number of levels for given student and course id */                                       
      end;                                                                                                                            
                                                                                                                                      
      do _n_ = 1 to _n_;                                                                                                              
        set have;                                                                                                                     
        flag = (counter ge 2); /* if counter >= 2 (i.e. student had both low and high course) mark flag with 1 */                     
        output;                                                                                                                       
      end;                                                                                                                            
                                                                                                                                      
      drop course clevel counter;                                                                                                     
    run;                                                                                                                              
                                                                                                                                      
    Up to 40 obs from WANT total obs=19                                                                                               
                                                                                                                                      
            COURSE_     STUDENT_                                                                                                      
    Obs      NAME          ID       FLAG                                                                                              
                                                                                                                                      
      1    BASL-0101    0000001       0                                                                                               
      2    BASM-0101    0000001       0                                                                                               
      3    TRCT-0601    0000001       0                                                                                               
      4    TRCT-0601    0000003       0                                                                                               
      5    TRCT-0601    0000004       0                                                                                               
      6    ESLA-0301    0000002       0                                                                                               
      7    ESLO-0301    0000002       0                                                                                               
      8    ESLW-0301    0000002       0                                                                                               
      9    TRCT-0601    0000005       0                                                                                               
     10    GEDM-0401    0000006       1                                                                                               
     11    GEDM-0501    0000006       1                                                                                               
     12    GEDM-0301    0000007       0                                                                                               
     13    GEDR-0301    0000007       0                                                                                               
     14    ESLO-0401    0000008       0                                                                                               
     15    ESLW-0401    0000008       0                                                                                               
     16    GEDM-0301    0000009       0                                                                                               
     17    GEDM-0301    0000010       1                                                                                               
     18    GEDM-0401    0000010       1                                                                                               
     19    GEDW-0301    0000010       0                                                                                               
                                                                                                                                      
