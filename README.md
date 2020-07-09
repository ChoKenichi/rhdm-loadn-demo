# rhdm-loadn-demo

Decison Central で作成した loan-demo のサンプル

REST アクセス例
$ curl -u rhdmAdmin:jbos000 \
     -d @post.json  -X POST \
     -H "content-type: application/json" \
    "http://localhost:8080/kie-server/services/rest/server/containers/instances/loan-demo_1.0.0-SNAPSHOT"

$ cat post.json
{
 "commands":[
    {"insert":{"object":{"com.myspace.loan_demo.Applicant":{
                            "creditScore":230,
                            "name":"Jim Whitehurst"}
                               },
              "out-identifier":"applicant" }
      },
    {"insert":{ "object":{ "com.myspace.loan_demo.Loan":{
                             "amount":2500,
                             "approved":false,
                             "duration":24,
                             "interestRate":1.5,
                             "reason":"申請データ"}
                                },
               "out-identifier":"loan" }
     },
    {"insert":{ "object":{ "com.myspace.loan_demo.Loan":{
                             "amount":25010,
                             "approved":false,
                             "duration":24,
                             "interestRate":1.5,
                             "reason":"申請データ2"}
                                },
               "out-identifier":"loan2" }
     },    {"fire-all-rules":{}}
 ]
}
