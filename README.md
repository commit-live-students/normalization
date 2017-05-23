![GitHub Logo](https://s3.ap-south-1.amazonaws.com/greyatom-social/GreyAtom-logo.png)

# Normalization

If a database design is not perfect, it may contain anomalies, which are like a bad dream for any database administrator. Managing a database with anomalies is next to impossible.

* ***Update anomalies*** − If data items are scattered and are not linked to each other properly, then it could lead to strange situations. For example, when we try to update one data item having its copies scattered over several places, a few instances get updated properly while a few others are left with old values. Such instances leave the database in an inconsistent state.
* ***Deletion anomalies*** − We tried to delete a record, but parts of it was left undeleted because of unawareness, the data is also saved somewhere else.
* ***Insert anomalies*** − We tried to insert data in a record that does not exist at all.

Normalization is a method to remove all these anomalies and bring the database to a consistent state.

<br />

### First Normal Form

First Normal Form is defined in the definition of relations (tables) itself. This rule defines that all the attributes in a relation must have atomic domains. The values in an atomic domain are indivisible units.

| Course | Content  |
| ------ | -------  |
| Programming | Java, C++ |
| WEB | Php, HTML, ASP |

We re-arrange the relation (table) as below, to convert it to First Normal Form.

| Course | Content  |
| ------ | -------  |
| Programming | Java |
| Programming | C++ |
| WEB | Php |
| WEB | HTML |
| WEB | ASP |

<br />

### Second Normal Form

Before we learn about the second normal form, we need to understand the following −

* ***Prime attribute*** − An attribute, which is a part of the prime-key, is known as a prime attribute.
* ***Non-prime attribute*** − An attribute, which is not a part of the prime-key, is said to be a non-prime attribute.

If we follow second normal form, then every non-prime attribute should be fully functionally dependent on prime key attribute. That is, if X → A holds, then there should not be any proper subset Y of X, for which Y → A also holds true.

Student_Project
| stu_id | pro_id  | stu_name  | pro_name  |
| ------ | -------  | -------  | -------  |

We see here in Student_Project relation that the prime key attributes are Stu_ID and Proj_ID. According to the rule, non-key attributes, i.e. Stu_Name and Proj_Name must be dependent upon both and not on any of the prime key attribute individually. But we find that Stu_Name can be identified by Stu_ID and Proj_Name can be identified by Proj_ID independently. This is called partial dependency, which is not allowed in Second Normal Form.

Student
| stu_id | pro_id  | stu_name  |
| ------ | -------  | -------  |

Project
| pro_id  | pro_name  |
| ------ | -------  |

<br />

### Third Normal Form
For a relation to be in Third Normal Form, it must be in Second Normal form and the following must satisfy −

* No non-prime attribute is transitively dependent on prime key attribute.
* For any non-trivial functional dependency, X → A, then either −
    * X is a superkey or,
    * A is prime attribute.

Student_Detail
| Stu_id | Stu_name | City | Zip |
| ------ | -------  | -------  | -------  |

We find that in the above Student_detail relation, Stu_ID is the key and only prime key attribute. We find that City can be identified by Stu_ID as well as Zip itself. Neither Zip is a superkey nor is City a prime attribute. Additionally, Stu_ID → Zip → City, so there exists transitive dependency.

To bring this relation into third normal form, we break the relation into two relations as follows −

Student_Detail
| Stu_id | Stu_name | Zip |
| ------ | -------  | -------  |

Zip_Codes
| Zip | City |
| ------ | -------  |
