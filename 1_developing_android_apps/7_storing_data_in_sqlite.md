## Storing data in SQLite

  1. Introduction
  2. Why SQLite?
  3. Quiz: SQL Query
  4. Waitlist ToyApp
  5. Creating the Contract
     - One of the main principles of SQL databases is the **schema**: a formal declaration of how the database is organized. 
     - You may find it helpful to create a companion class, known as a **contract class**, which explicitly specifies the layout of your schema in a systematic and self-documenting way.
     - *A contract class is a container for constants that define names for URIs, tables, and columns.*
     - The contract class allows you to use the same constants across all the other classes in the same package. This lets you change a column name in one place and have it propagate throughout your code.
  6. Running Unit Tests
  7. Exercise: Create the Contract
  8. Creating the database
  9. Exercise: Create The Database
  10. Querying All Guests
  11. Exercise: Query All Guests
  12. Updating the Adapter
  13. Exercise: Update The Adapter
  14. Adding Guests
  15. Exercise: Add Guests
  16. Removing Guests
  17. Exercise: Remove Guests
  18. Exercise: Sunshine Database
  19. Exercise: Invalid Inserts in
  20. Exercise: Resolve Conflicts