# utl-duplicate-each-column-using-the-prefix-B-for-the-copied-columns
Duplicate each column using the prefix B for the copied columns
    %let pgm=utl-duplicate-each-column-using-the-prefix-B-for-the-copied-columns;

    %stop_submission;

    Duplicate each column using the prefix B for the copied columns
    
    github
    https://tinyurl.com/adw777n8
    https://github.com/rogerjdeangelis/utl-duplicate-each-column-using-the-prefix-B-for-the-copied-columns

    sas communities
    https://tinyurl.com/mtdf9xym
    https://communities.sas.com/t5/SAS-Programming/PROC-SQL-DB-WITH-SAME-COLUMNS/m-p/730615#M227530

    /**************************************************************************************************************************/
    /* INPUT            | PROCESS                          | OUTPUT                                                           */
    /* data have;       | %array(                          |                    Added Columns                                 */
    /*   input          |  _new                            |                    -------------------                           */
    /*     name$        |  ,values=%utl_varlist(have));    |  NAME   SEX AGE    B_NAME  B_SEX B_AGE                           */
    /*     sex$ age;    |                                  |                                                                  */
    /* cards4;          | data want;                       | Alfred   M   14    Alfred    M     14                            */
    /* Alfred  M 14     |   merge have have(rename=(       | Alice    F   13    Alice     F     13                            */
    /* Alice   F 13     |    %do_over(_new,phrase=%str(    | Barbara  F   13    Barbara   F     13                            */
    /* Barbara F 13     |    ?=b_?)                        | Carol    F   14    Carol     F     14                            */
    /* Carol   F 14     |    )));                          | Henry    M   14    Henry     M     14                            */
    /* Henry   M 14     | run;quit;                        | James    M   12    James     M     12                            */
    /* James   M 12     |                                  |                                                                  */
    /* ;;;;             |                                  |                                                                  */
    /* run;quit;        |                                  |                                                                  */
    /**************************************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
