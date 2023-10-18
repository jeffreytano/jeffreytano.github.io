---
layout: single
title: "Entities"
permalink: /Learning/typeorm/
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