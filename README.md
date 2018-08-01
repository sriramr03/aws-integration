# aws-integration

## Spring Boot and AWS Integration

  * Steps to install and have local AWS Setup done

	• Check if Python is installed if not first install python 
	• python --version
	• Installation using PIP
	• pip --version (if not installed then install using below)
	• curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
	• python get-pip.py --user or python3 get-pip.py --user 
	• pip install awscli --upgrade --user or pip3 install awscli --upgrade --user
	• Or sudo pip install awscli --ignore-installed six
	• aws --version


### Local dynamoDB Setup Details:
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.html


#### commands from cli for dynamoDB

aws dynamodb list-tables --endpoint-url http://localhost:8000

You need to pass --endpoint-url to each aws cli command for dynamodb 

aws dynamodb create-table --table-name Customer --attribute-definitions AttributeName=guid,AttributeType=S AttributeName=customerId,AttributeType=S --key-schema AttributeName=customerId,KeyType=HASH AttributeName=guid,KeyType=RANGE --provisioned-throughput ReadCapacityUnits=1,WriteCapacityUnits=1 --endpoint-url http://localhost:8000


aws dynamodb put-item --table-name Customer --item '{"customerId": {"S": "1234"}, "guid": {"S": "123-456-789"}, "status": {"S": "inprogress"} }' --return-consumed-capacity TOTAL --endpoint-url http://localhost:8000

aws dynamodb query --table-name Customer --key-condition-expression 'guid = :a' --expression-attribute-values '{":a": {"S":"123-456-789"}}' --endpoint-url http://localhost:8000


aws dynamodb delete-table --table-name Customer --endpoint-url http://localhost:8000

### Ex. Spring Data Integration project
http://www.baeldung.com/spring-data-dynamodb 

Credits: www.baeldung.com

