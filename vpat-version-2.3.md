---
description: IllumiDesk's accessibility documentation.
---

# VPAT Version 2.3

## **Name of Product:** IllumiDesk

## **Date: January 2021**

Contact Information: [accessibility@illumidesk.com](mailto:accessibility@illumidesk.com)

**Notes:** IllumiDesk functions primarily as an integration between the Canvas LMS and Jupyter Notebooks. This report covers accessibility conformance for the IllumiDesk product available directly to end-users via the web application user interface, however, it does not cover accessibility conformance for the Learning Management System and Jupyter Notebooks directly. Nevertheless, this report does not discuss the design environment which is only used by designers of application processes and forms.

**Evaluation Methods Used:** Conformance to the listed accessibility standards has been evaluated by IllumiDesk using a combination of static analysis tools and manual testing with assistive technologies.

## **Applicable Standards/Guidelines**

This report covers the degree of conformance for the following accessibility standard/guidelines**:**

* **Revised Section 508 standards:** [https://www.section508.gov/manage/program-roadmap](https://www.section508.gov/manage/program-roadmap).
* **Web Content Accessibility Guidelines \(WCAG\) 2.0 \(Level A/AA\):** [https://www.w3.org/WAI/standards-guidelines/wcag/](https://www.w3.org/WAI/standards-guidelines/wcag/). WCAG 2.1 Level A/AA conformance is also documented herein.
* **Techniques for WCAG 2.0**: [https://www.w3.org/TR/WCAG20-TECHS/](https://www.w3.org/TR/WCAG20-TECHS/).

## **Terms**

The terms used in the Conformance Level information are defined as follows:

* **Supports:** The functionality of the product has at least one method that meets the criterion without known defects or meets with equivalent facilitation.
* **Partially Supports:** Some functionality of the product does not meet the criterion.
* **Does Not Support:** The majority of product functionality does not meet the criterion.
* **Not Applicable:** The criterion is not relevant to the product.

## **WCAG 2.1 Report**

This table documents conformance of IllumiDesk \(including web content, electronic documents, software components, and authoring systems\) with WCAG 2.1.

### **Table 1: Perceivable Information and user interface components must be presentable to users in ways they can perceive.**

| **WCAG 2 Success Criterion** | **Supports** | **Remarks and Explanations** |
| :--- | :--- | :--- |
| 1.1.1 Non-text Content | Partially supports | Most, but not all, non-text elements have equivalent text alternatives. |
| 1.2.1 Prerecorded Audio-only and Video-only | Supports | Time-based media was not encountered in the sample. |
| 1.2.2 Captions \(Prerecorded\) | Partially supports | Videos embedded within the application contain closed captioning \(CC\) in the English language only. |
| 1.2.3 Audio Description or Media Alternative \(Prerecorded\) | Partially supports | Videos embedded within the application are limited to the format provided. |
| 1.2.4 Captions \(Live\) | Partially supports | Live content is closed-captioned \(CC\) upon user request using text to speech tools and speech to text. |
| 1.2.5 Audio Description \(Prerecorded\) | Partially supports | Audio descriptions are provided in writing but do not always include summaries in video formats. |
| 1.3.1 Info and Relationships | Partially supports | Not all label and legend text is programmatically associated with form controls. |
| 1.3.2 Meaningful Sequence | Supports | The reading and navigation order is logical and intuitive. |
| 1.3.3 Sensory Characteristics | Supports | Instructions do not rely on shape, size, visual location, or sound. |
| 1.3.4 Orientation \(2.1\) | Supports | The orientation of web content is not restricted to only portrait or landscape. |
| 1.3.5 Identify Input Purpose \(2.1\) | Supports | Input fields do not have inappropriate autocomplete attributes. |
| 1.4.1 Use of Color | Partially supports | Meaning is sometimes conveyed by color alone. |
| 1.4.2 Audio Control | Supports | No audio content was encountered in the sample. |
| 1.4.3 Contrast \(Minimum\) | Partially supports | Some text has insufficient contrast. |
| 1.4.4 Resize text | Supports | The page is readable and functional when the page is zoomed to 200% |
| 1.4.5 Images of Text | Supports | No images of text were encountered in the sample. |
| 1.4.10 Reflow \(2.3\) | Partially supports | Some content is excessively justified to screen margins when dimensions are 320 pixels or less in width. However, no loss of content or functionality otherwise occurs. |
| 1.4.11 Non-text Contrast \(2.3\) | Supports | Graphical objects, user interface elements meet or exceed minimum 3:1 contrast. |
| 1.4.12 Text Spacing \(2.3\) | Supports | No loss of content or functionality occurs when the user adapts text spacing. |
| 1.4.13 Content on Hover or Focus \(2.3\) | Supports | No issues with additional content presented on hover/focus |

### 

### **Table 2: Operable User interface components and navigation must be operable.**

| **WCAG 2 Success Criterion** | **Supports** | **Remarks and Explanations** |
| :--- | :--- | :--- |
| 2.1.1 Keyboard | Partially supports | Most, but not all, content is keyboard accessible. |
| 2.1.2 No Keyboard Trap | Supports | No keyboard traps encountered. |
| 2.1.4 Character Key Shortcuts \(2.1\) | Does not support | No mechanism is present to disable the shortcut keys. |
| 2.2.1 Timing Adjustable | Partially supports | Some content disappears after a short time. |
| 2.2.2 Pause, Stop, Hide | Supports | No animated content encountered. |
| 2.3.1 Three Flashes or Below Threshold | Supports | Content does not flash. |
| 2.4.1 Bypass Blocks | Supports | The site has a functioning skip link. |
| 2.4.2 Page Titled | Supports | Pages have appropriate titles. |
| 2.4.3 Focus Order | Does Not Support | IllumiDesk does not support right to left languages. |
| 2.4.4 Link Purpose \(In Context\) | Supports | Link purpose can be determined from the link text, or from the link text in context |
| 2.4.5 Multiple Ways | Supports | Multiple navigation methods are available. |
| 2.4.6 Headings and Labels | Supports | Headings and labels describe topic or purpose. |
| 2.4.7 Focus Visible | Partially supports | Most elements have visible keyboard focus indicators. |
| 2.5.1 Pointer Gestures \(2.1\) | Supports | Content can be controlled without path-based gestures. |
| 2.5.2 Pointer Cancellation \(2.1\) | Supports | No mousedown or similar events encountered. |
| 2.5.3 Label in Name \(2.1\) | Supports | Interactive elements' visible labels are included in their accessible names. |
| 2.5.4 Motion Actuation \(2.1\) | Supports | No device movement was found to trigger functionality. |

### 

### **Table 3: Understandable Information and the operation of user interface must be understandable.**

| **WCAG 2 Success Criterion** | **Supports** | **Remarks and Explanations** |
| :--- | :--- | :--- |
| 3.1.1 Language of Page | Partially Supports | Some issues were encountered when attempting to determine what page language is specified |
| 3.1.2 Language of Parts | Supports | No alternate-language parts encountered. |
| 3.2.1 On Focus | Supports | Navigation is consistent, simple, and user-initiated. |
| 3.2.2 On Input | Supports | Form controls do not trigger page changes or navigation immediately when input is entered. |
| 3.2.3 Consistent Navigation | Supports | Navigation elements are consistent across the site. |
| 3.2.4 Consistent Identification | Supports | Functional elements are consistently identified. |
| 3.3.1 Error Identification | Supports | Accessible instructions and error messages are provided where needed. |
| 3.3.2 Labels or Instructions | Partially supports | Some issues were encountered with fieldset/legend structure. |
| 3.3.3 Error Suggestion | Partially supports | Most error messaging suggests ways to fix the input in a timely and accessible manner. |
| 3.3.4 Error Prevention \(Legal, Financial, Data\) | Supports | No legal, financial, or test data encountered. |

### 

### **Table 4: Robust Content must be robust enough that it can be interpreted reliably by a wide variety of user agents, including assistive technologies.**

| **WCAG 2 Success Criterion** | **Supports** | **Remarks and Explanations** |
| :--- | :--- | :--- |
| 4.1.1 Parsing | Supports | HTML validation issues do not impact accessibility. |
| 4.1.2 Name, Role, Value | Partially supports | ARIA attributes are often used where they are not needed. |

## **Functional Performance Criteria \(FPC\)**

| **Criteria** | **Conformance Level** | **Remarks and Explanations** |
| :--- | :--- | :--- |
| Without Vision | Supports | IllumiDesk has been optimized to work well with screen readers such as JAWS or VoiceOver. |
| With Limited Vision | Supports | IllumiDesk supports screen magnification and browser-provided zoom functionality. |
| Without Perception of Color | Supports | IllumiDesk support minimum contrast ratios  |
| Without Hearing | Supports | IllumiDesk does not use any audio for its default operation. Users can upload their own content and are responsible for ensuring the accessibility of the uploaded content. |
| With Limited Hearing | Supports | IllumiDesk does not use any audio for its default operation. Users can upload their own content and are responsible for ensuring the accessibility of the uploaded content. |
| Without Speech | Not Applicable | IllumiDesk does not require speech for operation. |
| With Limited Manipulation | Supports | IllumiDesk does not require fine motor control or simultaneous actions. It is accessible via keyboard and touch devices. |
| With Limited Reach and Strength | Supports | IllumiDesk does not require fine motor control or simultaneous actions. It is accessible via keyboard and touch devices. |
| With Limited Language, Cognitive, and Learning Abilities | Supports | IllumiDesk supports the adaptation of content by end-users and provides an easy-to-use interface for users with cognitive or learning disabilities. |

| **WCAG 2 Success Criterion** | Supports | Remarks and Explanations |
| :--- | :--- | :--- |
| 602.2 Accessibility and Compatibility Features | Partially Supports | Not all documentation is av. |
| 602.3 Electronic Support Documentation | Supports | Support documentation is located at https://docs.illumidesk.com |
| 602.4 Alternate Formats for Non-Electronic Support Documentation | Partially Supports | Users can export support documentation, such as user guides, to open formats. It is up to the user to print the documentation if needed. |

