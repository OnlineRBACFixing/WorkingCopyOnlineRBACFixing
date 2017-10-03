
# Datasets

## SmallComp

Dataset generated by simplyfing the paper working example to obtain optimal solution with a wide range of B values thus enabling the comparison with sub-otpimal solvers


|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/SC/UPA.txt)|
|User-to-role      |[PA](dataset/SC/UA.txt)  |
|Permission-to-Role | [UA](dataset/SC/PA.txt) |
|Exception List           | [excs](dataset/SC/excs.txt)| 


## Domino

Dataset benchmark used in Role-mining literature obtained from the user access profiles of the Lotus Domino Server.


|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/D/UPA.txt)|
|User-to-role      |[PA](dataset/D/UA.txt)  |
|Permission-to-Role | [UA](dataset/D/PA.txt) |
|Exception List           | [excs](dataset/D/excs.txt)| 


## University

Dataset benchmark used in Role-ming literature generated from a template at the Stony Brook University.


|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/U/UPA.txt)|
|User-to-role      |[PA](dataset/U/UA.txt)  |
|Permission-to-Role | [UA](dataset/U/PA.txt) |
|Exception List           | [excs](dataset/U/excs.txt)| 


## Firewall1

Dataset benchmark used in Role-ming literature representing policies implemented though firewalls used to provide external users access to internal resources. 


|Input| Link|  	   
|:-:	           |:---:	|
|Permission-to-User | [UPA](dataset/F/UPA.txt)|
|User-to-role      |[PA](dataset/F/UA.txt)  |
|Permission-to-Role | [UA](dataset/F/PA.txt) |
|Exception List           | [excs](dataset/F/excs.txt)| 





# Selection of a Max-SAT solver

## Complete Solvers

|Solver  	       |SmallComp  |Domino   	 |University   	|Firewall1   	|   	
|:-:	           |:---:	|:---:	|:---:	|:---:	|	
|_Maximo_   	   |[B<=0.65](CompleteS/SC/Maximo/Results.txt)   	   |[B<=0.05](CompleteS/D/Maximo/Results.txt)    	  |[B<=0.05](CompleteS/U/Maximo/Results.txt)   	| [B=0](CompleteS/F/Maximo/Results.txt)   	|   	
|_MaxHS_   	     |[B<=0.25](CompleteS/SC/MaxHS/Results.txt)     	   |[B<=0.2](CompleteS/D/MaxHS/Results.txt)   	      |[B<=0.2](CompleteS/U/MaxHS/Results.txt)    	| [B=0](CompleteS/F/MaxHS/Results.txt)   	|   	
|_Ahmaxsat_   	 |[B<=0.3](CompleteS/SC/Ahmaxsat/Results.txt)   	 |- | -  	|  - 	|   	
|_CCLS2akmaxsat_ |[B<=0.1](CompleteS/SC/CCLS2akmaxsat/Results.txt) |- |  - 	|  - 	|   	
|_CCEHC2akmaxsat_|[B<=0.1](CompleteS/SC/CCEHC2akmaxsat/Results.txt)|- | -  	| -  	|   	








## Incomplete Solvers

### Time complexity based on Firewall1 variant

90 online fixing instances of increasing size have been generated from _Firewall1_ by selecting more and more of its users (i.e., rows); each instance is associated with a single exception to incorporate and generates a Max-SAT encoding of growing size. 

|5 users (0.4 MB)|21 users (5.2 MB)|37 users (12.0 MB)|53 users (29.1 MB)|69 users (57.9 MB)|85 users (83.8 MB)|101 users (120.9 MB)|117 users (170.5 MB)|133 users (232.9 MB)|149 users (315.1 MB)|165 users (352.9 MB)|181 users (398.2 MB)|197 users (541.5 MB)|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|	
|[UA](dataset/complexity/89/UA.txt)|[UA](dataset/complexity/85/UA.txt)|[UA](dataset/complexity/81/UA.txt)|[UA](dataset/complexity/77/UA.txt)|[UA](dataset/complexity/73/UA.txt)|[UA](dataset/complexity/69/UA.txt)|[UA](dataset/complexity/65/UA.txt)|[UA](dataset/complexity/61/UA.txt)|[UA](dataset/complexity/57/UA.txt)|[UA](dataset/complexity/53/UA.txt)|[UA](dataset/complexity/49/UA.txt)|[UA](dataset/complexity/45/UA.txt)|[UA](dataset/complexity/41/UA.txt)|
|[PA](dataset/complexity/89/PA.txt)|[PA](dataset/complexity/85/PA.txt)|[PA](dataset/complexity/81/PA.txt)|[PA](dataset/complexity/77/PA.txt)|[PA](dataset/complexity/73/PA.txt)|[PA](dataset/complexity/69/PA.txt)|[PA](dataset/complexity/65/PA.txt)|[PA](dataset/complexity/61/PA.txt)|[PA](dataset/complexity/57/PA.txt)|[PA](dataset/complexity/53/PA.txt)|[PA](dataset/complexity/49/PA.txt)|[PA](dataset/complexity/45/PA.txt)|[PA](dataset/complexity/41/PA.txt)|
|[exc](dataset/complexity/89/excs.txt)|[exc](dataset/complexity/85/excs.txt)|[exc](dataset/complexity/81/excs.txt)|[exc](dataset/complexity/77/excs.txt)|[exc](dataset/complexity/73/excs.txt)|[exc](dataset/complexity/69/excs.txt)|[exc](dataset/complexity/65/excs.txt)|[exc](dataset/complexity/61/excs.txt)|[exc](dataset/complexity/57/excs.txt)|[exc](dataset/complexity/53/excs.txt)|[exc](dataset/complexity/49/excs.txt)|[exc](dataset/complexity/45/excs.txt)|[exc](dataset/complexity/41/excs.txt)|


![H_ResponseTime](img/H_responseTime.png)

The figure below shows the minimum timeout needed to obtain a feasible solution for these inputs as a function of their size. Minimum timeout needed to compute feasible solution to _Firewall1_ (y axis, secs) as a function of the number of users (x axis). Along the x-axis we also note the size of the corresponding CNF formula. The results are also available in plain text in [Results.txt](dataset/complexity/Results.txt)


### Quality of incomplete solutions

Experiment based on _SmallComp_ dataset to measure the ability of the incomplete solver adopted to satisfy the soft constraints. In particular, this is computed as the average weight of satisfied soft constraints over the total sum of weights for the 12 exceptions. 

![rateSoft](dataset/qualityIncomplete/rateSoft.png)

The figure above shows the average percentage of satisfied soft clauses (y axis) as a function of the balance B (c_axis) in the _SmallComp_ dataset

Results are also available in plain text in [rate.txt](dataset/Incomplete/rate.txt) which are based on the evalaution of the three configurations:
- complete solver [Results.txt](dataset/Incomplete/complete/Results.txt)
- incomplete solver (timeout 2 sec) [Results.txt](dataset/Incomplete/2/Results.txt)
- incomplete solver (timeout 180 sec) [Results.txt](dataset/Incomplete/180/Results.txt)



# Experimental Results 

## Impact of Beta

## Impact of timeout

## The order of exceptions





## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/OnlineRBACFixing/WorkingCopyOnlineRBACFixing/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image]("A_ratesoft.png")
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/OnlineRBACFixing/WorkingCopyOnlineRBACFixing/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
