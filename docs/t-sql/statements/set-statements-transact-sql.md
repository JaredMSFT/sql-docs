---
title: "SET Statements (Transact-SQL)"
description: SET Statements (Transact-SQL)
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.date: "03/14/2017"
ms.prod: sql
ms.prod_service: "sql-database"
ms.technology: t-sql
ms.topic: reference
f1_keywords:
  - "SET"
  - "SET_TSQL"
helpviewer_keywords:
  - "ISO SET statements"
  - "queries [SQL Server], executing"
  - "dates [SQL Server], SET statements"
  - "time [SQL Server], SET statements"
  - "SET statement, about SET statement"
  - "SET statement"
  - "statistical information [SQL Server], SET statements"
  - "locking [SQL Server], SET statements"
dev_langs:
  - "TSQL"
monikerRange: "=azure-sqldw-latest||=azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017"
---
# SET Statements (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

The [!INCLUDE[tsql](../../includes/tsql-md.md)] programming language provides several SET statements that change the current session handling of specific information. The SET statements are grouped into the categories shown in the following table.  
  
For information about setting local variables with the SET statement, see [SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
|Category|Statements|  
|--------------|----------------|  
|Date and time statements|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)<br /><br /> [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)|  
|Locking statements|[SET DEADLOCK_PRIORITY](../../t-sql/statements/set-deadlock-priority-transact-sql.md)<br /><br /> [SET LOCK_TIMEOUT](../../t-sql/statements/set-lock-timeout-transact-sql.md)|  
|Miscellaneous statements|[SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)<br /><br /> [SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)<br /><br /> [SET FIPS_FLAGGER](../../t-sql/statements/set-fips-flagger-transact-sql.md)<br /><br /> [SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md)<br /><br /> [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md)<br /><br /> [SET OFFSETS](../../t-sql/statements/set-offsets-transact-sql.md)<br /><br /> [SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md)|  
|Query Execution Statements|[SET ARITHABORT](../../t-sql/statements/set-arithabort-transact-sql.md)<br /><br /> [SET ARITHIGNORE](../../t-sql/statements/set-arithignore-transact-sql.md)<br /><br /> [SET FMTONLY](../../t-sql/statements/set-fmtonly-transact-sql.md)<br /> Note: [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br /><br /> [SET NOCOUNT](../../t-sql/statements/set-nocount-transact-sql.md)<br /><br /> [SET NOEXEC](../../t-sql/statements/set-noexec-transact-sql.md)<br /><br /> [SET NUMERIC_ROUNDABORT](../../t-sql/statements/set-numeric-roundabort-transact-sql.md)<br /><br /> [SET PARSEONLY](../../t-sql/statements/set-parseonly-transact-sql.md)<br /><br /> [SET QUERY_GOVERNOR_COST_LIMIT](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md)<br /><br /> [SET RESULT SET CACHING](../../t-sql/statements/set-result-set-caching-transact-sql.md?view=azure-sqldw-latest&preserve-view=true) (Preview)<br /> Note:  This feature applies to [!INCLUDE[ssSDW](../../includes/sssdwfull-md.md)] only.<br /><br /> [SET ROWCOUNT](../../t-sql/statements/set-rowcount-transact-sql.md)<br /><br /> [SET TEXTSIZE](../../t-sql/statements/set-textsize-transact-sql.md)|  
|ISO Settings statements|[SET ANSI_DEFAULTS](../../t-sql/statements/set-ansi-defaults-transact-sql.md)<br /><br /> [SET ANSI_NULL_DFLT_OFF](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)<br /><br /> [SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)<br /><br /> [SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md)<br /><br /> [SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md)<br /><br /> [SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md)|  
|Statistics statements|[SET FORCEPLAN](../../t-sql/statements/set-forceplan-transact-sql.md)<br /><br /> [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md)<br /><br /> [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md)<br /><br /> [SET SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md)<br /><br /> [SET STATISTICS IO](../../t-sql/statements/set-statistics-io-transact-sql.md)<br /><br /> [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)<br /><br /> [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)<br /><br /> [SET STATISTICS TIME](../../t-sql/statements/set-statistics-time-transact-sql.md)|  
|Transactions statements|[SET IMPLICIT_TRANSACTIONS](../../t-sql/statements/set-implicit-transactions-transact-sql.md)<br /><br /> [SET REMOTE_PROC_TRANSACTIONS](../../t-sql/statements/set-remote-proc-transactions-transact-sql.md)<br /><br /> [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)<br /><br /> [SET XACT_ABORT](../../t-sql/statements/set-xact-abort-transact-sql.md)| 
  
## Considerations When You Use the SET Statements  
  
- All SET statements run at execute or run time, except these statements, which run at parse time:

  - SET FIPS_FLAGGER
  - SET OFFSETS
  - SET PARSEONLY
  - and SET QUOTED_IDENTIFIER  
  
- If a SET statement runs in a stored procedure or trigger, the value of the SET option gets restored after the stored procedure or trigger returns control. Also, if you specify a SET statement in a dynamic SQL string that runs by using either **sp_executesql** or EXECUTE, the value of the SET option gets restored after control returns from the batch that you specified in the dynamic SQL string.  
  
- Stored procedures execute with the SET settings specified at execute time except for SET ANSI_NULLS and SET QUOTED_IDENTIFIER. Stored procedures specifying SET ANSI_NULLS or SET QUOTED_IDENTIFIER use the setting specified at stored procedure creation time. If used inside a stored procedure, any SET setting is ignored.  
  
- The **user options** setting of **sp_configure** allows for server-wide settings and works across multiple databases. This setting also behaves like an explicit SET statement, except that it occurs at login time.  
  
- Database settings set by using ALTER DATABASE are valid only at the database level and take effect only if explicitly set. Database settings override instance option settings that are set by using **sp_configure**.  
  
- If a SET statement uses ON and OFF, you can specify either one for multiple SET options.
  
    > [!NOTE]  
    >  This doesn't apply to the statistics related SET options.
  
     For example, `SET QUOTED_IDENTIFIER, ANSI_NULLS ON` sets both QUOTED_IDENTIFIER and ANSI_NULLS to ON.  
  
- SET statement settings override identical database option settings that are set by using ALTER DATABASE. For example, the value specified in a SET ANSI_NULLS statement will override the database setting for ANSI_NULLs. Additionally, some connection settings get automatically set ON when a user connects to a database based on the values that go into effect by the previous use of the **sp_configure user options** setting, or the values that apply to all ODBC and OLE/DB connections.  
  
- ALTER, CREATE and DROP DATABASE statements don't honor the SET LOCK_TIMEOUT setting.  
  
- When a global or shortcut SET statement sets several settings, issuing the shortcut SET statement resets the previous settings for all those options that the shortcut SET statement affects. If a SET option that gets affected by a shortcut SET statement gets set after the shortcut SET statement gets issued, the individual SET statement overrides the comparable shortcut settings. An example of a shortcut SET statement would be SET ANSI_DEFAULTS.  
  
- When batches are used, the database context is determined by the batch that is established by using the USE statement. Unplanned queries and all other statements that run outside the stored procedure and that are in batches inherit the option settings of the database and connection established by the USE statement.  
  
- Multiple Active Result Set (MARS) requests share a global state that contains the most recent session SET option settings. When each request executes, it can modify the SET options. The changes are specific to the request context in which they're set, and don't affect other concurrent MARS requests. However, after the request execution is completed, the new SET options are copied to the global session state. New requests that execute under the same session after this change will use these new SET option settings.  
  
- When a stored procedure runs from a batch or from another stored procedure, it's run under the option values set up in the database that has the stored procedure. For example, when stored procedure **db1.dbo.sp1** calls stored procedure **db2.dbo.sp2**, stored procedure **sp1** executes under the current compatibility level setting of database **db1**, and stored procedure **sp2** executes under the current compatibility level setting of database **db2**.  
  
- When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement concerns objects that are in multiple databases, the current database context and the current connection context applies to that statement. In this case, if [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is in a batch, the current connection context is the database defined by the USE statement; if the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is in a stored procedure, the connection context is the database that contains the stored procedure.  
  
- When you're creating and manipulating indexes on computed columns or indexed views, you must set these SET options to ON: ARITHABORT, CONCAT_NULL_YIELDS_NULL, QUOTED_IDENTIFIER, ANSI_NULLS, ANSI_PADDING, and ANSI_WARNINGS. Set the option NUMERIC_ROUNDABORT to OFF.  
  
  If you don't set any one of these options to the required values, INSERT, UPDATE, DELETE, DBCC CHECKDB, and DBCC CHECKTABLE actions on indexed views or tables with indexes on computed columns will fail. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will raise an error listing all the options that are incorrectly set. Also, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will process SELECT statements on these tables or indexed views as if the indexes on computed columns or on the views don't exist. 

- When SET RESULT_SET_CACHING is ON, it enables the result caching feature for the current client session.   Result_set_caching cannot be turned ON for a session if it is turned OFF at the database level.    When SET RESULT_SET_CACHING is OFF, the result set caching feature is disabled for the current client session. Changing this setting requires membership in the public role.
Applies to: [!INCLUDE[ssSDW](../../includes/sssdwfull-md.md)] Gen2
