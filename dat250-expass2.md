Notes for expass2.md in other repo
- The database is stored in-memory database, in which it the configuration can be found within the `persistence.xml` file. In `CreditCardsMain.java`, it is the `EntityManager` which interacts with the database. 

- Hibernate creates the SQL based on class entity, set `hibernate.show_sql` to `true` in the `persistence.xml` file.
```
Hibernate: 
    create table Customer (
        id bigint generated by default as identity,
        name varchar(255),
        primary key (id)
    )
```

- The main issue experienced when implementing these classes were when the objects were compared for equality in the test cases. Here the test case checks for a `Set`. Which produceses a fairly tricky error messange when running the tests, ex: 

`assertThat(bank.getOwnedCards(), is(Set.of(firstCard, secondCard)));`

Initially caused the error message:

```
CreditCardsMainTest.testDomainModelPersistence:71 
Expected: is <[no.hvl.dat250.jpa.tutorial.creditcards.CreditCard@641ed324, no.hvl.dat250.jpa.```tutorial.creditcards.CreditCard@45984654]>
     but: was <[no.hvl.dat250.jpa.tutorial.creditcards.CreditCard@641ed324, no.hvl.dat250.jpa.tutorial.creditcards.CreditCard@45984654]>
```

A quickfix for this issue after insepection was returning the collection in its required form.
```
public Set getOwnedCards() {
   return Set.copyOf(ownedCards);
}
```