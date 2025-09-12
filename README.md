# utl-duplicate-each-column-using-the-prefix-B-for-the-copied-columns
    %let pgm=utl-duplicate-each-column-using-the-prefix-B-for-the-copied-columns;

    %stop_submission;

    TWO SOLUTIONS

     1 Ted Clay Array
     2 Bart Baseplus Package
       Bartosz Jablonski yabwon@gmail.com
       https://github.com/yabwon/SAS_PACKAGES
       made a small change added '_character_'
       %getVars(&have.,varRange=_numeric_ _character_);

    Duplicate each column using the prefix B for the copied columns

    github
    https://tinyurl.com/adw777n8
    https://github.com/rogerjdeangelis/utl-duplicate-each-column-using-the-prefix-B-for-the-copied-columns

    sas communities
    https://tinyurl.com/mtdf9xym
    https://communities.sas.com/t5/SAS-Programming/PROC-SQL-DB-WITH-SAME-COLUMNS/m-p/730615#M227530

    /**************************************************************************************************************************/
    /* INPUT            | PROCESS                          | OUTPUT                                                           */
    /*                  |                                  |                                                                  */
    /*                  | 1 TED CLAY ARRAY                 |                                                                  */
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
    /* ;;;;             | 2 BART BASEPLUS PACKAGE          |                                                                  */
    /* run;quit;        |   see below                      |                                                                  */
    /*                  |                                  |                                                                  */
    /**************************************************************************************************************************/

    /*___    _                _     _                          _
    |___ \  | |__   __ _ _ __| |_  | |__   __ _ ___  ___ _ __ | |_   _ ___
      __) | | `_ \ / _` | `__| __| | `_ \ / _` / __|/ _ \ `_ \| | | | / __|
     / __/  | |_) | (_| | |  | |_  | |_) | (_| \__ \  __/ |_) | | |_| \__ \
    |_____| |_.__/ \__,_|_|   \__| |_.__/ \__,_|___/\___| .__/|_|\__,_|___/
                                                        |_|
    */
     /*-- i have already installed packages --*/
    filename packages "C:\SAS_PACKAGES";

    /*--- bootstrap macros                  --*/
    %include "c:/sas_packages/SPFinit.sas";

    /*
    %helpPackage(basePlus,'%getVars()')
    %helpPackage(basePlus,'%zipEvalf()')
    */

    %loadPackage(BasePlus)

    %let have=sashelp.class;

    %let list=%getVars(&have.,varRange=_numeric_ _character_);
    %put &=list;

    LIST=NAME SEX AGE HEIGHT WEIGHT

    data want;
      set &have.;
      set &have.(rename=(
      %zipEvalf(&list., &list., function=catx, argBf==ABB_)
    ));
    run;

    %put #&list.#;
    %put #%zipEvalf(&list., &list., function = catx, argBf==ABC_)#;

    Rename code
    #AGE=ABC_AGE HEIGHT=ABC_HEIGHT WEIGHT=ABC_WEIGHT#

    /**************************************************************************************************************************/
    /* WORK.WANT                                   |  Addded Columns                                                          */
    /*                                             |  --------------------------------------------------                      */
    /*                                             |                                     ABB_      ABB_                       */
    /*  NAME       SEX    AGE    HEIGHT    WEIGHT  |  ABB_NAME    ABB_SEX    ABB_AGE    HEIGHT    WEIGHT                      */
    /*                                             |                                                                          */
    /*  Alfred      M      14     69.0      112.5  |  Alfred         M          14       69.0      112.5                      */
    /*  Alice       F      13     56.5       84.0  |  Alice          F          13       56.5       84.0                      */
    /*  Barbara     F      13     65.3       98.0  |  Barbara        F          13       65.3       98.0                      */
    /*  Carol       F      14     62.8      102.5  |  Carol          F          14       62.8      102.5                      */
    /*  Henry       M      14     63.5      102.5  |  Henry          M          14       63.5      102.5                      */
    /*  James       M      12     57.3       83.0  |  James          M          12       57.3       83.0                      */
    /*  Jane        F      12     59.8       84.5  |  Jane           F          12       59.8       84.5                      */
    /*  Janet       F      15     62.5      112.5  |  Janet          F          15       62.5      112.5                      */
    /*  Jeffrey     M      13     62.5       84.0  |  Jeffrey        M          13       62.5       84.0                      */
    /*  John        M      12     59.0       99.5  |  John           M          12       59.0       99.5                      */
    /*  Joyce       F      11     51.3       50.5  |  Joyce          F          11       51.3       50.5                      */
    /*  Judy        F      14     64.3       90.0  |  Judy           F          14       64.3       90.0                      */
    /*  Louise      F      12     56.3       77.0  |  Louise         F          12       56.3       77.0                      */
    /*  Mary        F      15     66.5      112.0  |  Mary           F          15       66.5      112.0                      */
    /*  Philip      M      16     72.0      150.0  |  Philip         M          16       72.0      150.0                      */
    /*  Robert      M      12     64.8      128.0  |  Robert         M          12       64.8      128.0                      */
    /*  Ronald      M      15     67.0      133.0  |  Ronald         M          15       67.0      133.0                      */
    /*  Thomas      M      11     57.5       85.0  |  Thomas         M          11       57.5       85.0                      */
    /**********************************************|***************************************************************************/


    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
