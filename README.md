Web accessibility means that people with disabilities can use the Web.

Reasons developers should learn accessibility
It's fun!
We're the ones making it inaccessible
Human Rights
Legal Issue
Reach a larger audience
Impactful
Makes you a specialist

Accessibility Standards
Web Content Accessibility Guidelines (WCAG)
WCAG specifies three different conformance levels they are:
A (lowest)
AA (mid range)
and AAA (highest)

Screen readers convert digital text into synthesized speech. They empower users to hear content and navigate with the keyboard. The technology helps people who are blind or who have low vision to use information technology with the same level of independence and privacy as anyone else.
           <img src="https://pbs.twimg.com/media/KSJHECKJH983er.jpg" alt="A puppy in the park" />

           user has to upload an image:
           <img src="https://pbs.twimg.com/media/KSJHECKJH983er.jpg" alt="" />
           empty alt tag

HTML labels
A better option is to use the HTML label tag which will allow screen readers to recite the label when the field is focused.

        <form>
            <label for="first">First Name</label>
            <input id="first" type="text" />
            <label for="last">Last Name</label>
            <input id="last" type="text" />
            <label for="password">Password</label>
            <input id="password" type="password" />
            <input type="submit" value="Submit" />
          </form>

Limitations with the <label> tag
The label tag can only works with "labelable" elements. Those include:

<button>
<input>
<keygen>
<meter>
<output>
<progress>
<select>
<textarea>

f you ever need to label an element not on that list, use aria-label instead.
<div aria-label="Interactive div">Hello</div>

Screenreader only content
Sometimes you'll want to communicate with a screen reader directly! One cool example is announcing to screen reader users that you offer accessibility features! In that case you can make some HTML and wrap it in a visually hidden class.

        
          .visuallyhidden {
            position: absolute;
            left: 0;
            top: -500px;
            width: 1px;
            height: 1px;
            overflow: hidden;
          }
    

Live Regions
Applications can become very dynamic. For cases where important information could be coming in at any time, the ARIA spec provides the ability to mark an element as containing live data so that screen readers can read out updates as they come.

Think of using the Uber app to hail a ride. At first your status will be "waiting for a ride" but at an undetermined time it will change to "drive en route". For this we could:

        
          <div aria-live="assertive">Waiting for a ride</div>
        
      
Then, all we have to do is update the content of that div and any assistive technology will let the user know.

One of my favorite APIs, the value that you pass in to aria-live is a politeness setting. You can pass in:

assertive - will interrupt whatever it's doing to announce.
polite - will announce the live region update when it next idles.
off - will not read the update.