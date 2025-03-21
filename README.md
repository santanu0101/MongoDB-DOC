# Mongodb

Mongodb is a NoSQL (non-relational) database. IT stroes data in a type of JSON format Called **BSON**.

## Database

A database is a collection of data stored in a format that can easily be accessed.

## NOSQL Database

```mongodb
<!-- -----------------collection----------------- -->

<!-- document 1 -->
{
    name: "Ram Kumar",
    age: 21,
    gender: "MALE"
}

<!-- document 2 -->
{
    name: "Ram Kumar",
    age: 21,
    gender: "MALE"
}
```

## Datatype

| JSON | BSON (Binary JSON)     |
| :-------- | :------- |
| `String` | `String` | 
| `Number` | `Double` | 
| `Boolean` | `32bit and 64bit Integer` | 
| `Array` | `Boolean` | 
| `Object` | `Array` | 
| `Null` | `Object` | 
|| `Null` | 
|| `Regular Expression` | 
|| `Timestamp` | 
|| `Date` | 
|| `ObjectId` | 

#

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar.

```bash
pip install foobar
```

## Usage

```python
import foobar

# returns 'words'
foobar.pluralize('word')

# returns 'geese'
foobar.pluralize('goose')

# returns 'phenomenon'
foobar.singularize('phenomena')
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)