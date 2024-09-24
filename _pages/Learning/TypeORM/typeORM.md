---
layout: single
title: "Entities"
permalink: /learning/typeorm/
classes: wide
sidebar:
  nav: Learning
---

### Type ORM table template

let table name to be `Client`
```
import {Entity, BaseEntity} from "typeorm"

@Entity('client') // table name in the database
export class Client extends BaseEntity {

    @PrimaryColumn() // Primary key column
    id: number

    @Column() //Specify a column with column name and datatype
    name: string;
    
    @Column(
        {unique: true} //column decorator - unique specify the column should be unique
        ) 
    name: string;

    @CreateDataColumn // (optional) special column that generate timestamp of creation time
    created_at: Date;

    @UpdateDataColumn // (optional) special column that generate timestamp of update time
    updated_at: Date;

    @OneToMany(){
      () => Transaction,
      transaction => transaction.client
    }``
    transactions = Transaction[] //Client(one) to Transaction(many)

    @ManyToMany(
      () => Banker
    )
    bankers: Banker[]
}

```

```
import {Client} from './Client'

@Entity('transaction') // table name in the database
export class Transaction extends BaseEntity {

    @PrimaryColumn() // Primary key column
    id: number

    @Column() //Specify a column with column name and datatype
    name: string;
    
    @ManyToOne(
      () => Client, // First direction: The Many to One, return the target table
      client => client.transactions // Second direction: The One to Many
    )

    @JoinColumn({ //Only put joinColumn on the foreign key side , i.e. the many side in this case.
      name: 'client_id' //
    })
    client: Client // {target}:{targetType}
}
```

```
@Entity('Banker') // table name in the database
export class Transaction extends BaseEntity {

    @PrimaryColumn() // Primary key column
    id: number

    @ManyToMany(
      () => Client
    )

    @JoinTable({ //Create table for many-to-many
      name: "bankers_clients, // name of the table
      joinColumn: { // self join new table
        name: "banker",
        referencedColumnName: 'id' // take self table column as reference
      },
      inverseJoinColumn: { //opponent join new table
        name: "client",
        referenceColumnName: 'id' 
      }
    })
    clients: Client[]

}
```

### Column decorator [Reference](https://orkhan.gitbook.io/typeorm/docs/decorator-reference#column-decorators){: .btn .btn--info}{:target="\_blank"}

| Decorator | data type | Remark 
|:-
| unique | boolean | column is unique
| length | string / number | column type length (exact i think?)
| nullable | boolean | column is nullable
| update | boolean | column is not updatable
| type | string | use type instead of typescript type
| default | type of the column | provide default value
| name | string | name of column in database
| enum | enum type | limit the value in the enum

### Columns
| Column | Remark 
|:-
| @Column() | Ordinary column
| @PrimaryColumn() | Column with primary key
| @PrimaryGeneratedColumn() | Auto generated primary column
| @CreateDataColumn() | Special column that generate timestamp of creation time
| @UpdateDataColumn() | Special column that generate timestamp of update time
| @ManyToOne() | 
| @OneToMany() | 
| @ManyToMany() |
| @JoinColumn() | 
| @JoinTable() | Used on Many-to-many relationship

### Example

Get request
```
const router = express.Router()
....

router.get("/", (req,res) =>{ // "/" defines the api endpoint
  Client.find().then((data)=>{  // "Client" <-- "entity"
    res.json(data);
  });
})
```

Post request
```
router.post("/", async (req,res) => {
  const{
    first_name,
    lastname,
    email,
  } = req.body;

  const client = Client.create({
    first_name,             // if the variable name is the same, just write the name
    last_name : lastname,   // if the variable name is not the same, write like this
    email,
  })

  await client.save()
  return res.json(client)   // just a respond, any format is ok
})
```