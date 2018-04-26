# BlockStampr YellowPaper

### *BlockStampr* chaincode application

#### Members and roles

  * **Customer**: Orders a *product*, a *model* or a specific *design*
  * **Designer**: Conceives a *design*, by it's own initiative or with the input of a customer, possibly by modifying or aggregating other *designs*
  * **Maker**: Offers one or several *models* of a designs, builds and delivers *products*

#### Database structure

  * **Design** Any form of object plan, 3D model, etc
  
```
designX_uid: {
	hash: "0db44f",
	uri: "https://www.thingiverse.com/thing:2477694"
}
```

  * **Model** A design with specific attributes

```
modelY_uid: {
	design: "designX_uid",
	attributes: {
		"color": "green"
		"wood": "pine",
		"price": 1000
	}
}
```

  * **Product** A built model


#### Chaincode commands

##### Invocations

  * **Conceive**

```
Command
-------
  designer_x,user_y?: <'conceive', design*>

Result
------
  design_uid
```

  * **Offer**

```
Command
-------
  maker_x,user_y?: <'offer', design, attributes>

Result
------
  model_uid
```

  * **Order**

```
Command
-------
  maker_x,user_y: <'order', model>

Result
------
  product_uid
```

  * **Deliver**

```
Command
-------
  maker_x,user_y: <'deliver', product>

Result
------
  product_uid
```


##### Queries

  * **Browse**
  
```
designer -> design*
```

  * **Catalog**

```
maker -> model*
```

  * **History**

```
product -> transaction*
```
