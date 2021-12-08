# Class Methods
## CSV Files

When we would like to extend our code and add some more features, then we might have a hard time adding those features because the actual **data** and the **code** are maintained in the same location, ie- the same python file. 

So to solve this problem you could use what is called a CSV file. 
* You could store your values as **comma seperated values** where each line will represent a single strucured data.
* **CSV** is a great opton here because it allows the data to be saved in a table structured format.
* A csv file is created with a file name followed by the extension `.csv`
* Now, we go ahead and write some _csv_ content into the file, that will help us to represent the same data we had previously.

### Content Stored in items.csv
```
name,price,quantity
"Noodles",15,10
"Chocolate",5,12
"Biryani",100,3
"Pulaav",70,5
"Naan",25,8
```
* The first line represents the columns that we are going to have for the data we are going to maintain.

### Reading data from csv file

* We are going to create a method inside our class to read the data from csv file
* But, now the problem is we are not going to have any instances in our hand to call this method.
* Because the method we are going to create is actually designed for instantiating the object itself. So this means that this method could not be called from an instance.
* So we are going to solve this by converting the method into a **class method**.
    * A **class method** can be accessed in the class level itself. So to access a class method there is no need to create an object. Hence, problem solved! :)
    * Inorder to convert a method into a class method, we use a _**decorator**_ &rarr;    `@classmethod`
        * **Decorators** in Python is just a quick way to change the behaviour of the functions what we write by basically calling them just before the line that we create our function.
> Note:  
> * An object can also access  the class attributes and the class methods.
```python
# Contd..
    def apply_discount(self):
            self.price -= self.price * self.discount 

    @classmethod
    def instantiate(cls):
        with open("items.csv", "r") as f:
            reader = csv.DictReader(f)
            items = list(reader)

        for item in items:
            print(item)

    def __repr__(self):
        return f"{self.__class__.__name__}(\"{self.name}\", {self.price}, {self.quantity})"

Item.instantiate()
```
* The class method still receives one parameter by default. ie- `cls`
* When we call our class methods, the class object itself is passed as the first argument always in the background.

Now, coming back to our method..
* We open our csv file using a context manager which is:
```python
with open("items.csv", "r") as f:
```
* Under this block, we use the method to directly read the CSV file which converts the contents into a dictionary object. To use this method, we need to `import` the csv library.

```python
    reader = csv.DictReader(f)
```
* To read the data from the dictionary object, we convert it into a list and iterate over the list with the help of a for-loop.
```python
    items = list(reader)
for item in items:
    print(item)
```
> Output:
```
OrderedDict([('name', 'Noodles'), ('price', '15'), ('quantity', '10')])
OrderedDict([('name', 'Chocolate'), ('price', '5'), ('quantity', '12')])
OrderedDict([('name', 'Biryani'), ('price', '100'), ('quantity', '3')])
OrderedDict([('name', 'Pulaav'), ('price', '70'), ('quantity', '5')])
OrderedDict([('name', 'Naan'), ('price', '25'), ('quantity', '8')])
```
Now, we have the data ready. The only thing left is to create the instances.
### Creating instances with data from csv file
```python
    @classmethod
    def instantiate(cls):
        with open("items.csv", "r") as f:
            reader = csv.DictReader(f)
            items = list(reader)

        for item in items:
            Item(
                name = item.get('name'), 
                price = float(item.get('price')), 
                quantity = int(item.get('quantity'))
            )
                        
    def __repr__(self):
        return f"{self.__class__.__name__}(\"{self.name}\", {self.price}, {self.quantity})"

Item.instantiate()
print(Item.array)
```
* Now, for each item in the list, we create an instance by calling the default constructor
```python
Item(
    name = item.get('name'),
    price = float(item.get('price')),
    quantity = int(item.get('quantity'))
)
```
* `<dictionary>.get(<key>)` is a dictionary method used to get the _value_ of the key specified.
* And one more point to keep in mind. When reading from csv files, Python stores the content as _strings_. 
    * Since, we expect _price_ to be a float and _quantity_ to be an integer, we convert them.
* In the next line, we print our **array of objects** to check if our instances has been created successfully.

```python
print(Item.array)
```