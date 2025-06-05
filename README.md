# rise-interview-question

Explanation of the Issue
The issue was caused by two problems:
1. Button Type: The <button> was defined with type="button", which does not trigger a form's onSubmit event. For form submission to work, the button must have type="submit".
   
2. Missing Function Call: In e.preventDefault, the parentheses () were missing, so the function wasn’t actually being executed.

How I Investigated It
I started by adding a console.log() inside the handleSubmit function to check if it was being triggered. When clicking the button, nothing happened, which told me the event handler wasn't firing. I then inspected the button element and noticed it was using type="button" instead of submit. Changing it to type="submit" allowed the form's onSubmit to be triggered as expected. I also corrected the missing parentheses in e.preventDefault().

Here is the solution below

## ✅ Fixed Code

```jsx
export default function FeedbackForm() {
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Form submitted');
  };

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit Feedback</button>
    </form>
  );
}
