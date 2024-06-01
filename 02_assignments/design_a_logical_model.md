# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

![image](https://github.com/YuriyKoshulap/sql/assets/94837852/a8fd0253-3ad9-47ff-b249-b4468f715fb3)


## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

![image](https://github.com/YuriyKoshulap/sql/assets/94837852/4bdfb91f-d2cc-4cd8-9162-0e4d6c785c08)


## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Type 1 SCD overwrites old data with new data. The schema of such table would presuppose that each customer has a foreign key linking to their physical address, so that when a customer’s address changes, it's updated with the new address.

Customer: customer_id, phys_address_id, mail_address_id
Address: customer_id, street, city, zip, country

Type 2 SCD retains historical changes by creating new records. Address table keeps all prvious address records.
Customer: customer_id
Address_type: customer_id, mail_address_id, address_type, start_date, end_date
Address: customer_id, street, city, zip, country

Bonus: Are there privacy implications to this, why or why not?
```
Yes, because continuous storage of sales records in a db can bring the personal data breach in the event of data leakage. So a timely destruction of personal data is a best practice.
```

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
AdventureWorks 2008 schema is much more elaborate as the organization is bigger than a small bookstore. It incorporates product vendor details, which my ERD lacks. My ERD could benefit from a "supplier/publishing_house" table to monitor the origins of books and efficiently manage incoming shipments. Product review in the AdventureWorks 2008 schema is something i would like to have as customer feedback is a great way to improve the quality of a service.

```

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `June 1, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
