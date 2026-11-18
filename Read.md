IAM USER = CLI

Step #1 -		OPEN CMD in your local system 
 		type command = aws –version
		if not installed then install using below link
		https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#getting-started-install-instructions

    <img width="841" height="141" alt="image" src="https://github.com/user-attachments/assets/c4236371-5d79-400c-a6bc-848e54f7c2b0" />

Step #2 -		Creating access for CLI 
 	Note – Access Keys (access key and secret key): interact with aws service programmatically (via CLI and SDK) 

Step #3 - 	Creating access key for IAM User we created 
 		Go to - Root account – IAM – IAM users – open user – security credentials – Access key – create Access key 

    <img width="1144" height="248" alt="image" src="https://github.com/user-attachments/assets/4b7c17bf-e1ff-42b8-83f5-5202a63c323e" />
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Step #4 - 	Create Access Key = interface – selected CLI as our use key is that

    <img width="914" height="357" alt="image" src="https://github.com/user-attachments/assets/e2531647-72d8-453b-a83a-832862b15b65" />

 Step #5 - 	When key is created 

 <img width="809" height="276" alt="image" src="https://github.com/user-attachments/assets/fe8dcca7-9e30-4f9a-83f0-cd06f6989359" />

      Note: - we can skip and add these after creating a user

Step #6 - 	open command prompt 
 		type command - aws configure
 		it will ask Aws ID - 
 		It will ask Access key -  
 		default region - 
 		default format - 

    <img width="1109" height="108" alt="image" src="https://github.com/user-attachments/assets/6fceeb87-2502-41b4-b607-60c2789a3ffb" />

 
Step #7 -		Check command in aws – we can see access denied because we have not given permission to IAM user 

 <img width="1109" height="102" alt="image" src="https://github.com/user-attachments/assets/c0c42cb6-0347-446b-b959-2bef27d09304" />


Step #8 - 	Step#12 - 	Adding permissions to IAM after login – IAM user – ADD permission
 
<img width="714" height="350" alt="image" src="https://github.com/user-attachments/assets/1c4b66c9-77cb-46c1-b132-6b85baa81ad4" />

  
Step #9- 		Adding permission in user which is read only = IAMReadOnlyAccess
	 
 
<img width="1144" height="444" alt="image" src="https://github.com/user-attachments/assets/881d2d41-dc46-4ec1-98f8-5c7a229bf78a" />

<img width="1144" height="227" alt="image" src="https://github.com/user-attachments/assets/c94edd32-2329-4e5b-9046-302200ccc9a9" />

Step#10- now we can check in CLI – we can able to list users

<img width="899" height="530" alt="image" src="https://github.com/user-attachments/assets/a721996e-b108-4d63-bcd5-9be9b047ac15" />

 	

