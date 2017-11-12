## Content Providers

  1. Introduction
  2. Content Providers
     - Content providers can help an application **manage access to data** stored by itself, stored by other apps, and provide a way to share data with other apps. 
     - They encapsulate the data, and provide mechanisms for defining data security.
       - ![content-providers](https://developer.android.com/guide/topics/providers/images/content-provider-overview.png)
       - You implement a content provider if you want to share your app's data with other applications.
       - In addition to that, you need your own content provider in the following cases:
         - You want to implement custom search suggestions in your application
         - You need to use a content provider to expose your application data to widgets
         - You want to copy and paste complex data or files from your application to other applications
  3. Content Provider Advantages
  4. DroidTermsExample
  5. Exercise: Setup QuizExample
  6. Content Provider Permissions
  7. Exercise: Add the Permission
  8. The Content Resolver
  9. Four Basic Operations
  10. Uniform Resource Identifier
  11. Quiz: TVTime
  12. Solution: TVTime
  13. Quiz: Actor Query
  14. Solution: Actor Query
  15. Quiz: Calendar Provider
  16. Solution: Calendar Provider
  17. Calling the ContentProvider
  18. Exercise: Make an AsyncTask
  19. Structure of the Data
  20. Working with Cursors Review
  21. Exercise: Use the Cursor
  22. Solution: Use the Cursor
  23. Conclusion