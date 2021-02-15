# Unimelb COMP20008 Elements of Data Processing Summary


## Some points
- Version: 2019 Semester 1
- Lecturer: [James Bailey](https://people.eng.unimelb.edu.au/baileyj/) and [Pauline Lin](https://cis.unimelb.edu.au/people/pauline-lin)
- This is a beginning course for Data Science
- Programming part focus on data wrangling using python


## Lecture 1 Introduction
- **Data Wrangling**
	- What is data wrangling
	- What activities the it encompasses
	- Why it is done
	- Why it is challenging
	- Why it is useful
	- Appreciate the series of activities in data wrangling (the data wrangling pipeline)



## Lecture 2 & 3 Data Formats
- **Data formats**
	- Structured: Relational Database, CSV
	- Unstructured: text
	- Semi-structured: HTML, XML, JSON
- **Benefits for having structure of data**
	- Easier to analyse, easier to query
	- Easier to store
	- Easier to clean, maintain consistency and security, especially with multiple users
- **Comma Separated Value(CSV)**
	- Spreadsheet
	- Easy to use
	- Structured, but not like a relational DB
- **Difference between CSV and spreadsheet**
	- CSV is a plain text format. Spreadsheet often refers to XLS file which is a binary file format
- **Text**
	- No Structure
	- Hard to index
	- Hard to organize
	- Lacks regularity and decomposable internal structure
- **Regular Expression**
	- Syntax
		- '.'    Any characters
		- '^'   Beginning of a string
		- '$'   End of a string
		- '\*'  Zero or more repetitions
		- '\+'  One or more repetitions
		- '|'     The or operator, used in conjunction with parentheses()
		- '[]'    A set of characters, e.g. [abcd], [a-zA-Z]
		- '[^]' Complement of a set of characters
			- [^a-z] matches any characters except a-z
		- Group text with parentheses
			- xy|z != x(y|z)
		- '()' Groups text
		- 'JA' The pattern: 'J' immediately followed by 'A'
		- 'JA*' The pattern: 'J' followed by zero or more occurence of 'A'
		- '(J|A)*' Zero or more repetitions of 'J' or 'A's
		- '(J|A)+' One or more repetitions of 'J' or 'A's
		- Email format:   [a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+(\.[a-zA-Z0-9-]+)+
	- **HTML(HyperText Markup Language)**
		- Markup with elements, delineated by start and end tags. Elements correspond to logic units such as heading, paragraph or itemised list
		- Tags: Keywords contained in pairs of angle brackets
		- Browser determines how to display/present the logical units
		- Not all elements need both start and end tags
		- Some elements can have attributes. The order of attributes is not important
		![html illustration](Image/html.png)
	- **Limitation of HTML**
		- HTML was designed for pure presentation
		- HTML is concerned with formatting not meaning
		- HTML is not extensible
			- can't be modified to meet specific domain knowledge
			- browsers have developed their own tags
		- HTML can be inconsistently applied
			- almost everything is rendered somehow
	- **XML(Extensible Markup Language)**
		- Extensible: Users define tags
		- Facilitate better encoding of semantics
		- It was designed to store and transport data
		- It was designed to be self-descriptive
		- XML files must begin with declaration
			`<?xml version="1.0"?>`
		-  XML elements
			- Start/end tags or Empty tags
			- Attributes in quotes
				- \<campus> Parkville \</campus>
				- \<campus location = "Parkville" />
			- Appropriately nested
			- One root element
		- Comments
			- `<!-- comments do not affect the document -->`
		- Some characters have special meaning
			- '<' and '&' are strictly illegal inside an element
		- CDATA(character data) section may be used inside XML element to include large blocks of text, which may contain these special characters such as &, >
	- **(Exam Question)Difference between HTML and XML**
		- XML was developed to describe data and focalise on what the data represent; HTML was developed to display data and foculise on the way data looks
		- XML is about describing information; HTML is about displaying information
		- XML is extensible, users have possibility to define personal structures and tags; The tags and structures of HTML are predefined
	- **(Exam Question)Purpose of XML namespace**
		- To avoid name conflicts by differentiating elements and attributes within an XML document that may have identical name but different definitions
	- **Namespace Scope**
		- The scope of a namespace declaration is
			- The element that contains the namespace declaration
			- All its descendants(i.e. nested within the element)
			- The declaration may be overridden by further nested namespace declarations
		- Namespaces can be used to describe *both elements and attributes*. Elements without a namespace prefix are defined a default namespace
	- **XML schema & validation**
		- An XML file can be well-formed and NOT valid; it is valid if it is consistent with a particular schema
		- XML Schema languages, example:
			- XSD(XML Schema Definitions): a W3C standard
			- DTD(Document Type Definitions)
		- HTML5 schema for Web browser <!DOCTYPE html>
	- **XML parsers**
		- Document Object Model(DOM)
			- Programming interface for XML and HTML
			- Most useful way of parsing XML
			- Parsing calls load the document into a tree structure with different nodes that can be navigated by the program
		- Simple API for XML (SAX)
			- Stream-based way of reading XML (sequential)
			- Fast and efficient if you don't need random-access
			- Memory efficient
	- **JSON(JavaScript Object Notation)**
		- Object data is in name/value pairs
			- "firstName" : "John"
		- JSON values
			- A number (integer or floating point)
			- A string (in double quotes)
			- A Boolean (true or false)
			- An array (in square brackets)
			- An object (in curly braces)
			- null
			![JSON_syntax](Image/JSON_syntax.png)
	- **(Exam Question)Comparison between JSON and XML**
		- JSON is simpler and more compact/lightweight than XML. Easy to parse
		- Common JSON application - read and display data from a web server using Javascript
		- XML comes with a large family of other standards for querying and transforming (XQuery, XML Schema, XPATH, XSLT, namespaces, ...)
		- XML allows complex schema definitions (via regular expressions)
			- allows formal validation
			- makes you consider the data design more closely
		- JSON is more streamlined, lightweight and compressed
			- Which appeals to programmers looking for speed and efficiency
			- widely used for storing data in noSQL databases
	- **JSON Schema**
		- Written in JSON itself
		- Describes the structure of other data
		- Easy to validate a JSON document against its schema using a schema validator



## Lecture 4 & 5 Data cleaning: missing values and outliers detection & Recommender Systems
- **Types of outliers**
	- Global outlier (or point anomaly)
		- Object is Og if it significantly deviates from the rest of the data set
	- Contexture outlier (or conditional outlier)
		- Object is Oc if it deviates significantly based on a selected context
- **How to detect outliers?**
	- 1-D data
		- Boxplot
		- Histogram
		- Statistical test
	- 2-D data
		- Scatter plot and eye ball
	- 3-D data
		- Also scatter plot and eye ball
	- \> 3-D data
		- Statistical and algorithmic methods
- **Recommender Systems**
	- Each user has a profile
	- User rates items
		- Explicit: Give a score
		- Implicit: Web usage mining
			- Time spent in viewing the item
			- Navigation path
	- System do the rest
- **Collaborative filtering**
	- Make predictions about a user's missing data according to the behaviour of many other users
		- Look at users *collective* behaviour
		- Look at the active user *history*
		- Combine
	- Approaches
		- User based methods
			- Identify like-minded users
		- Item based methods
			- Identify similar items
		- Model (Matrix) based methods
			- Simultaneously identify like-minded users and items
- **User based methods**
	- Achieve good quality in practice
	- The more processes we push offline, the better the method scale
	- However:
		- User preference is *dynamic*
			- High update frequency of offline-calculated information
		- No recommendation for *new users*
- **Item based methods**
	- Search for similarities among items
	- All computation can be *done offline*
	-  Item-item similarity is more stable than user-user similarity
		- No need for frequent update
	- Two phases
		- Offline phase. For each item
			- Determine its k-most similar items
			- Can use the same type of similarity as for user-based
		- Online phase.
			- Predicting rating raj for a given user-item pair as a weighted sum over the k-most similar items that they rated



## Lecture 6: Data visualisation
- **Motivation for data visualisation**
	- Converting data into a visual formats
		- Reveals characteristics of the data, relationship between objects or relationship between features
		- Simplifies the data
	- Humans are very good at analysing information in visual formats
		- Spot trends, patterns, outliers
		- Visualisation can help show data quality
	- Visualisation helps tell a story
- **Histogram**
	- Usually shows the distribution of a single variable
	- Divide the values into bins and show a bar plot of the number of objects in each bin
	- The number of each bar indicates the number of objects
	- Shape of histogram depends on number of bins
- **Heat maps**
	- Plot the data matrix
	- This can be useful when objects are sorted according to class/type
	- Typically, features are normalised to prevent one attribute from dominating the plot
- **Parallel Coordinates**
	- Used to plot the feature value of high-dimensional data
	- Instead of using perpendicular axes, use a set of parallel axes
	- The *feature value* of each object are plotted as a point on each corresponding coordinates axis and the points are connected by a line
	- Thus, *each object* is represented as a line
	- Often, the lines representing a distinct class of objects group together, at least for some features
	- Ordering of attributes is important in seeing such groupings
	- Scaling axes: Affect visualisation. May choose to scale all features into the range [0,1] via preprocessing step
	- Ordering of axes: Influences the relationship that can be seen. Correlation between pairs of features may only be visible in certain ordering



## Lecture 7: Clustering and clustering visualisation



## Lecture 8: Hierarchical clustering and dimension reduction



## Lecture 9: Assessing correlations



## Lecture 10: Mutual information



## Lecture 11: Guest Lecture
- **Not Examinable**



## Lecture 12 & 13: Classification and regression techniques: decision tree and k-nearest neighbor



## Lecture 14: No Lecture(Good Friday)
- **No Content**



## Lecture 15 & 16: Blockchain and data processing
- **Benefits of Blockchain**
	- No central, trusted point of control
	- Less administration, less bureaucracy
	- Less expensive
	- Faster transactions
	- More control over records handed to users
	- Ability to be anonymous
	- Users can verify data in the blockchain
	- No single point of failure
	- More secure solutions
- **Details**
	- The public ledger is called the blockchain(a file)
	- File is a sequence of blocks, each block contains a *header* and some *data* (list of transactions)
	- Block ID is equal to a hash of its header
	- Each block contains ID of its parent block
	- A block header typically includes:
		- *ID* of its parent block
		- *Timestamp* of block's creation
		-  *Hash of the data* (list of transactions) inside a block
- **How to make information in blockchain private**
	- Apply hash to the fact then adds this *hash output* to the blockchain along with a digital signature
		- No on can reverse the hash function to uncover the fact
		- Now stored on blockchain but privacy is preserved
	- Alternatively, could *encrypt the fact* using user's public key
	- Others can *apply hash* to the fact and see what is stored on the blockchain. They can also verify the fact was *digitally signed* by the owner
- **Blockchain usage in Health**
	- Patient data is added to the blockchain
		- Each visit to the doctor
		- Blood Test
		- ...
	- Data is encrypted with patients' public key
		- Patients may provide private key to insurer or health provider so they can review their medical history. Reduced time, fuller information available and quicker
- **Blockchain usage in Education**
	- Cheap, secure, shared resource to store credentials and microcredential
	- Uses Blockcerts system - software that is built on top of the bitcoin(financial) blockchain, and which allows education credential information to be stored
	- For university:
		- Secure
		- Easy to access
		- Less expensive
		- Store micro-credential
	- For student:
		- Don't need extra copies
		- Cheap
	- Employer:
		- Doesn't need to talk to university
		- Trust (security)



## Lecture 17: Guest Lecture
- **Not Examinable**



## Lecture 18 & 19 & 20: Data linkage and privacy
- **Data Linkage**
	- Combining related/equivalent records across the data source
		- Information relating to the same entity (e.g. a person or a place) is connected
- **Pipeline**
	- Prep
		- Clean records
	- Block
		- Represents complex records as simple values (blocks)
		- Only score records with simple value (block) in common
		- Each record from A allocated to one or more blocks
		- Each record from B allocated to one or more blocks
		- Within each block, compare the records from A against those from B and find those that match
		- If two records are not assigned to the same block, it means we believe they are not match
	- Score
		- Compare two records: assess their similarity
		- Score record pairs for similarity
	- Match
		- Match "sufficiently match" records  
	- Merge
		- Merge matched records
		- Resolve conflicting attributes
- **When do we need data linkage privacy**
	- Matched data is being passed to another organization or being made public; Data matching is conducted across databases from different organizations
		- How to solve: Without revealing any information about individuals who do not get linked across the databases (i.e., individuals who occur in one database and not in other)
		- We will need methods for computing similarity of records, without revealing the record values
			- Hashing is an important tool
				- A hash function H maps a data item of arbitrary size to a data item of fixed size
				- Non invertible (One way) hash function: Given the output H(X), extremely hard to reconstruct X.
			- We can represent numbers using different bases
- **Hash encoding for exact matching: 2 party protocol**
	- Each organization
		- Applies a (one way) hash function to the attributes used to join the databases
		- Shares its hashed values with the other organization. Each checks which one match. These are linked records.
	- Disadvantages
		1. Single character difference results in completely different output
		2. An organization can mount a dictionary attack to "invert" the hash function
- **Hash encoding for exact matching: 3 party protocol**
	- Involve a trusted 3rd party (Organization C)
	- Organization A and B send their hashed value to Organization C, who then checks for match.
	- What if Organization C is malicious
		- Organization C could mount a dictionary attack and guess hashed values
		- Solution: A and B perform "*dictionary attack resistant*" hashing. Organization A and B concatenate a secret word to every name field in their data before hashing (known as a salt). Organization C does not know what this word is and thus can't perform a dictionary attack to "reverse" the hashed value it received
	- Frequency Attack
		- The third party scheme may prevents a dictionary attack, but may still be susceptible to a frequent attack
		- 3rd party compares the distribution of hashed values to some known distribution
			- E.g. distribution of surname frequencies in a public database versus distribution of hash values. Then may be able to guess some of the hashed values
		- Organization A and B could prevent this by adding some random records to manipulate the frequency distribution
-  **Challenges**
	1. The hash based technique using the third party, can only compute exact similarity between strings in a privacy preserving manner. What if we wish to compute approximate similarity between two strings in a privacy preserving manner
	2. Public release: Suppose organizations wish to make one of its internal datasets public for social good purpose. It can be very, very difficult to prevent data linkage attacks or reverse engineering of people's identities
		Solution: Do not release at all!! or
		Release an obfuscated version of data (e.g. with noise added to all the records). This is the basis of methods such as *k-anonymity and differential privacy*
- **Summary for preserving privacy linkage**
	- Organization A and B can determine which records in the two databases are an exact match in a privacy preserving manner by
		- using trusted third party C
		- using one way hash function with salt
		- adding random records
	- A reasonably private scheme depends on how much the third party is trusted
- **A privacy preserving method for data linkage using approximate matching**
	- Components that are needed
		1. Computing *approximate similarity* of two record fields (strings)
		2. Representing a record field (string) in a privacy preserving manner (so that it is difficult to reverse engineer its value)
		3. Computing approximate similarity of two record fields (strings) that have been represented in privacy preserving manner
	- Issues
		- 1.Approximate Similarity
			![Approximate similarity](Image/Approx_similarity.png)
			Similarity measure can be easily extended to 3-grams, 4-grams ... (q-grams)
		- 2.Bloom Filters
			- bit string: an array of binary digits (bits): 0's and 1's
			- A bloom filter is an array of I bits, with all bits initially set to zero
			- We may store strings in the bloom filter by using hash functions H1 ... Hk to turn on certain bits
				- Each hash function Hi (1 <= i <= k) maps an input string X to a value in the range [0, I-1]
				- To store a string X in the bloom filter, set array index Hi(X) in the bloom filter to value '1', for each Hi(X)
			- Checking
				- For any string X, we can check if it is stored in the bloom filter by hashing X using the k hash functions
				- If at least one of the bits having value Hi(X) is set to 0, then X is definitely not a member of the bloom filter
				- If all of the bits having value Hi(X) are set to 1, then X appears to be a member of the bloom filter. However, it might not really be a member (a false positive)
			- Compare two strings for approximate similarity
				- There are two strings. The 2-grams of the first string are stored in bloom filter B1, the 2-grams of the second string are stored in bloom filter B2. Both bloom filters are the *same length and use the same hash functions*
				- If the two strings have a lot of 2-grams in common, then their bloom filters will have a large number of identical bit positions set to 1
		- 3.Similarity of bloom filters
			- ![Similarity for bloom filter](Image/bloom_filter_similarity.png)
			- Need a threshold value for deciding whether match or not



## Lecture 21: Public data release and individual anonymity
- **Measures of anonymity for individuals**
	- Removing explicit identifiers from a dataset is not enough
    - Solutions
     	- k-anonymity
       	- I-diversity
	- Terminology
		- Explicit Identifier: unique for an individual
			- name, national ID, Tax File Number, account number
		- Quasi-identifier: A combination of non sensitive attributes that can be linked with external data to identify an individual
			- E.g. {Gender, Age, Zip code} combination from earlier
		- Sensitive attributes: Information that people don't wish to reveal
			- E.g. Medical condition
- **k-anonymity**
	- Produce a release of the data with scientific guarantees that the individuals who are the subjects of the data cannot be re-identified while the data remain practically useful
	- A table satisfies k-anonymity if every record in the table is indistinguishable from at least k-1 other records with respect to every set of quasi-identifier attributes; such a table is called k-anonymous table
	- Hence, for every combination of values of the quasi-identifiers in the k-anonymous table, there are at least k records that share those values
	- How to achieve k-anonymity
		- Generalisation
			- Make the quasi identifiers less specific
			- Column level
		- Suppression
			- Remove (suppress) the quasi identifiers completely
			- Moderate the generalization process
			- Limited number of outliers
			- Row, column and cell level
	- If the worst case, if the data gets into wrong hands, can only narrow down a quasi identifier to a group of k individuals
	- Data publisher needs to
		- Determines quasi-identifiers
		- Choose parameter k
	- Attack on k-anonymity
		- 1.Homogeneity Attack: k-anonymity can create groups that leak information due to lack of diversity in the sensitive attribute
		- 2.Background Attack: k-anonymity does not protect against attacks based on background knowledge
		- Solution: Make the sensitive attribute diverse with each group
			- I-diversity: For each k anonymous group, there are at least I different sensitive attribute values
- **Summary**
	- To reduce risk of re-identification of individuals in released datasets
		- Choose value of k
		- Manipulate data to make k-anonymous, either
			- Replace categories by broader categories
			- Suppose attributes with a * (limited utility)
		- Further manipulate data to make it I-diverse
			- Ensure there are at least l different values of the sensitive attribute in each group
	- Privacy is difficult to maintain in high-dimensional datasets like trajectory datasets
		- Cloaking provides spatial k-anonymity
		- Obfuscation ensures location imprecision


## Lecture 22: Differential privacy
- **Local differential privacy**
	- Each person is responsible for adding noise to their own data. Classic survey example each person has to answer a question "Do you use drug?"
		- They flip a coin in secret and answer "Yes" if it comes up heads, but tell the truth otherwise
		- Plausible deniability about "Yes" answer
- **Global differential privacy**
	- We have a sensitive dataset, a trusted data owner Alice and researcher Bob. Alice does analysis on the raw data, adds noise to the answers, and reports the (noisy) answers to Bob
	- Global systems generally more accurate, and less noise is needed
	![Differential Privacy](Image/differential_privacy.png)
	- The privatized analysis comprises two steps
		- 1.Query the data and obtain the real result, e.g., how many female students are in the survey?
		- 2.Add random noise to hide the presence/absence of any individual. Release noisy result to the user
		![Add Random Noise](Image/add_random_noise.png)
	- The released results will be different each time (different amount of noised added)
- **The promise of differential privacy**
	- The chance that the noise released result will be R is nearly the same, whether or not an individual participates in the dataset
	![Promise](Image/promise_differential_privacy.png)
- **How much noise should we add to the result depends on**
	- *Privacy loss budget*: How private we want the result to be (How hard the attacker to guess the true result)
		- We want that the presence or absence of a user in the dataset does not have a considerable effect on the released result
		- ![privacy loss budget](!privacy_loss_budget_1.png)
		- Privacy loss budget = k (k > 0)
		- Choose k to guarantee that A <= 2^k * B
			- k = 0: No privacy loss (A = B), low utility
			- k = high: Large privacy loss, higher utility
			- k = low: Low privacy loss, lower utility
	- *Global sensitivity*: How much difference the presence or absence of an individual could make to the result
		- Global sensitivity of Query Q is the maximum difference in answers that adding or removing any individual from dataset can cause (maximum effect of an individual)
		- Intuitively, we want to consider the worst case scenario
		- If asking multiple queries, global sensitivity is equal to the sum of the differences  
- **Strategy**
	- Add noise to the according to *released result = True result + noise*
		- Where noise is a number randomly sampled from a distribution having 	
			- average value = 0
			- standard deviation (spread) = G/k
- **Summary**
	- Differential privacy guarantees that the presence or absence of a user cannot be revealed after releasing the query result
		- It does not prevent attackers from drawing conclusions about individuals from aggregate results over the population
	- We need to determine the budget and global sensitivity to know what is the scale of the noise to be added



## Lecture 23: Ethical consideration



## Lecture 24: Wrap up
- **No New Content**
