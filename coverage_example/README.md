Coverage is used as an approximation of testing capability. A bug cannot be detected if its buggy code is not executed. This is an example in TiDB:

issue:https://github.com/pingcap/tidb/issues/40015

fix commit: https://github.com/pingcap/tidb/commit/cfe9703a7f2195417b4384c7b7bfa3de1dbe485a

![image-20230413141646479](/home/hzy/hzydata/projects/db/impomysql_binary/coverage_example/README.assets/image-20230413141646479.png)

We can see that this bug is caused by an unhandled exception in `expression/builtin_time.go #3195`.

PINOLO can cover `expression/builtin_time.go #3195` (see ./tidb_pinolo.html):

![image-20230413142732723](/home/hzy/hzydata/projects/db/impomysql_binary/coverage_example/README.assets/image-20230413142732723.png)

TLP can not cover `expression/builtin_time.go #3195` (see ./tidb_tlp.html):

![image-20230413142856437](/home/hzy/hzydata/projects/db/impomysql_binary/coverage_example/README.assets/image-20230413142856437.png)

If the lines that trigger the bug are not covered, it is natural that the bug cannot be detected. Therefore, TLP cannot detect the bug mentioned above.