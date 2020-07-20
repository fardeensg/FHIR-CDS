---
title: Task Implementation Guidance
keywords: task, rest,
tags: [rest,fhir,api]
sidebar: ctp_rest_sidebar
permalink: api_task.html
summary: Task resource implementation guidance
---
​
{% include custom/search.warnbanner.html %}

​
## Task: Implementation Guidance ##
​
### Usage ###
The [Task](http://hl7.org/fhir/STU3/task.html) resource will be populated where there is a specific action for the intended recipient of the encounter report.

Detailed implementation guidance for a `Task` resource within the scope of this implementation guide is given below:  
​
​
<table style="min-width:100%;width:100%">
<tr>
    <th style="width:10%;">Name</th>
    <th style="width:5%;">Cardinality</th>
    <th style="width:10%;">Type</th>
      <th style="width:38%;">FHIR Documentation</th>
   <th style="width:37%;">CDS Implementation Guidance</th>
</tr>
<tr>
  <td><code>id</code></td>
    <td><code>0..1</code></td>
    <td>id</td>
    <td>Logical id of this artifact</td>
	<td></td>
</tr>
<tr>
  <td><code>meta</code></td>
    <td><code>0..1</code></td>
    <td>Meta</td>
    <td>Metadata about the resource</td>
		<td></td>
</tr>
<tr>
  <td><code>implicitRules</code></td>
    <td><code>0..1</code></td>
    <td>uri</td>
    <td>A set of rules under which this content was created</td>
		<td></td>
</tr>
<tr>
  <td><code>language</code></td>
    <td><code>0..1</code></td>
    <td>code</td>
    <td>Language of the resource content. <br /> <a href="http://hl7.org/fhir/STU3/valueset-languages.html">Common  Languages</a> (Extensible but limited to <a href="http://hl7.org/fhir/stu3/valueset-languages.html">All Languages</a>)</td>
	<td></td>
</tr>
<tr>
  <td><code>text</code></td>
    <td><code>0..1</code></td>
    <td>Narrative</td>
    <td>Text summary of the resource, for human interpretation</td>
	<td></td>
</tr>
<tr>
  <td><code>contained</code></td>
    <td><code>0..*</code></td>
    <td>Resource</td>
    <td>Contained, inline Resources</td>
	<td></td>
</tr>
<tr>
  <td><code>extension</code></td>
    <td><code>0..*</code></td>
    <td>Extension</td>
    <td>Additional Content defined by implementations</td>
	<td></td>
</tr>
<tr>
  <td><code>modifierExtension</code></td>
    <td><code>0..*</code></td>
    <td>Extension</td>
    <td>Extensions that cannot be ignored</td>
	<td></td>
</tr>
<tr>
  <td><code>identifier</code></td>
    <td><code>0..*</code></td>
    <td>Identifier</td>
    <td>Business identifier</td>
<td></td>
</tr>
<tr>
  <td><code>definition[x]</code></td>
    <td><code>0..1</code></td>
    <td></td>
    <td>Formal definition of task</td>
<td></td>
</tr>
<tr>
  <td class="sub"><code>definitionUri</code></td>
    <td></td>
    <td>uri</td>
    <td></td>
<td></td>
</tr>
<tr>
  <td class="sub"><code>definitionReference</code></td>
    <td></td>
    <td>Reference(ActivityDefinition)</td>
    <td></td>
<td></td>
</tr>
<tr>
  <td><code>basedOn</code></td>
    <td><code>0..*</code></td>
    <td>Reference(Any)</td>
    <td>Request fulfilled by this task</td>
<td>This SHOULD be the associated ReferralRequest.</td>
</tr>
<tr>
  <td><code>groupIdentifier</code></td>
    <td><code>0..1</code></td>
    <td>Identifier</td>
    <td>Requisition or grouper id
</td>
<td></td>
</tr>
<tr>
  <td><code>partOf</code></td>
    <td><code>0..*</code></td>
    <td>Reference(Task)</td>
    <td>Composite task</td>
<td></td>
</tr>
<tr>
  <td><code>status</code></td>
    <td><code>1..1</code></td>
    <td>code</td>
    <td>draft | requested | received | accepted | +<br>
<a href="http://hl7.org/fhir/STU3/valueset-task-status.html">TaskStatus</a> (Required)</td>
<td></td>
</tr>
<tr>
  <td><code>statusReason</code></td>
    <td><code>0..1</code></td>
    <td>CodeableConcept</td>
    <td>Reason for current status</td>
<td></td>
</tr>
<tr>
  <td><code>businessStatus</code></td>
    <td><code>0..1</code></td>
    <td>CodeableConcept</td>
    <td>E.g. "Specimen collected", "IV prepped"</td>
<td></td>
</tr>
<tr>
  <td><code>intent</code></td>
    <td><code>1..1</code></td>
    <td>code</td>
    <td>proposal | plan | order +<br>
<a href="http://hl7.org/fhir/STU3/valueset-request-intent.html">RequestIntent</a> (Required)</td>
<td></td>
</tr>
<tr>
  <td><code>priority</code></td>
    <td><code>0..1</code></td>
    <td>code</td>
    <td>routine | urgent | asap | stat<br>
<a href="http://hl7.org/fhir/STU3/valueset-request-priority.html">RequestPriority</a> (Required)</td>
<td>This MUST carry the value 'routine'.</td>
</tr>
<tr>
  <td><code>code</code></td>
    <td><code>0..1</code></td>
    <td>CodeableConcept</td>
    <td>Task Type: ambulance | cpcs | validation <a href="https://fhir.nhs.uk/STU3/ValueSet/UEC-TaskCode-1">UEC-TaskCode-1</a> (Extensible)</td>
<td>This MUST be populated.
</td>
</tr>
<tr>
  <td><code>description</code></td>
    <td><code>0..1</code></td>
    <td>string</td>
    <td>Human-readable explanation of task</td>
<td></td>
</tr>
<tr>
  <td><code>focus</code></td>
    <td><code>0..1</code></td>
    <td>Reference(Any)</td>
    <td>What task is acting on</td>
<td>This MUST NOT be populated.</td>
</tr>
<tr>
  <td><code>for</code></td>
    <td><code>0..1</code></td>
    <td>Reference(Any)</td>
    <td>Beneficiary of the Task</td>
<td>This MUST be the associated Patient.</td>
</tr>
<tr>
  <td><code>context</code></td>
    <td><code>0..1</code></td>
    <td>Reference(Encounter | EpisodeOfCare)</td>
    <td>Healthcare event during which this task originated</td>
<td>This MUST be the associated Encounter.</td>
</tr>
<tr>
  <td><code>executionPeriod</code></td>
    <td><code>0..1</code></td>
    <td>Period</td>
    <td>Start and end time of execution</td>
<td>This MUST be null at the creation of the encounter report.</td>
</tr>
<tr>
  <td><code>authoredOn</code></td>
    <td><code>0..1</code></td>
    <td>dateTime</td>
    <td>Task Creation Date</td>
<td>This MUST be populated.</td>
</tr>
<tr>
  <td><code>lastModified</code></td>
    <td><code>0..1</code></td>
    <td>dateTime</td>
    <td>Task Last Modified Date</td>
<td></td>
</tr>
<tr>
  <td><code>requester</code></td>
    <td><code>0..1</code></td>
    <td>BackboneElement</td>
    <td>Who is asking for task to be done</td>
<td>This SHOULD be the initiating user of the Encounter, i.e. the user of the EMS.</td>
</tr>
<tr>
  <td class="sub"><code>agent</code></td>
    <td><code>1..1</code></td>
    <td>Reference(Device | Organization | Patient | Practitioner | RelatedPerson)</td>
    <td>Individual asking for task</td>
<td></td>
</tr>
<tr>
  <td class="sub"><code>onBehalfOf</code></td>
    <td><code>0..1</code></td>
    <td>Reference(Organization)</td>
    <td>Organization individual is acting for</td>
<td>Only to be populated if requester.agent is a Practitioner.</td>
</tr>
<tr>
  <td><code>performerType</code></td>
    <td><code>0..*</code></td>
    <td>CodeableConcept</td>
    <td>requester | dispatcher | scheduler | performer | monitor | manager | acquirer | reviewer<br>
<a href="http://hl7.org/fhir/STU3/valueset-task-performer-type.html">TaskPerformerType</a> (Preferred)</td>
<td></td>
</tr>
<tr>
  <td><code>owner</code></td>
    <td><code>0..1</code></td>
    <td>Reference(Device | Organization | Patient | Practitioner | RelatedPerson)</td>
    <td>Responsible individual</td>
<td>This MUST be populated with the Organisation that is receiving the Task.</td>
</tr>
<tr>
  <td><code>reason</code></td>
    <td><code>0..1</code></td>
    <td>CodeableConcept</td>
    <td>Why task is needed</td>
<td>This MUST NOT be populated.</td>
</tr>
<tr>
  <td><code>note</code></td>
    <td><code>0..*</code></td>
    <td>Annotation</td>
    <td>Comments made about the task</td>
<td>See <a href="#note">additional guidance</a> below.</td>
</tr>
<tr>
  <td><code>relevantHistory</code></td>
    <td><code>0..*</code></td>
    <td>Reference(Provenance)</td>
    <td>Key events in history of the Task</td>
<td>If populated this MUST be the same as ReferralRequest.relevantHistory.</td>
</tr>
<tr>
  <td><code>restriction</code></td>
    <td><code>0..1</code></td>
    <td>BackboneElement</td>
    <td>Constraints on fulfillment tasks</td>
<td></td>
</tr>
<tr>
  <td class="sub"><code>repetitions</code></td>
    <td><code>0..1</code></td>
    <td>positiveInt</td>
    <td>How many times to repeat</td>
<td>In practice this will usually be set to one repetition.</td>
</tr>
<tr>
  <td class="sub"><code>period</code></td>
    <td><code>0..1</code></td>
    <td>Period</td>
    <td>When fulfillment sought</td>
<td>Time period in which the Task must be fulfilled - note that this will normally be different (shorter) than <code>ReferralRequest.occurrence</code></td>
</tr>
<tr>
  <td class="sub"><code>recipient</code></td>
    <td><code>0..*</code></td>
    <td>Reference(Patient | Practitioner | RelatedPerson | Group | Organization)</td>
    <td>For whom is fulfillment sought?</td>
<td>This MUST NOT be populated.</td>
</tr>
<tr>
  <td><code>input</code></td>
    <td><code>0..*</code></td>
    <td>BackboneElement</td>
    <td>Information used to perform task</td>
<td></td>
</tr>
<tr>
  <td class="sub"><code>type</code></td>
    <td><code>1..1</code></td>
    <td>CodeableConcept</td>
    <td>Label for the input</td>
<td></td>
</tr>
<tr>
  <td class="sub"><code>value[x]</code></td>
    <td><code>1..1</code></td>
    <td><a href="http://hl7.org/fhir/STU3/datatypes.html#open">*</a></td>
    <td>Content to use in performing the task</td>
<td></td>
</tr>
<tr>
  <td><code>output</code></td>
    <td><code>0..*</code></td>
    <td>BackboneElement</td>
    <td>Information produced as part of task</td>
<td>This MUST NOT be populated.</td>
</tr>
<tr>
  <td class="sub"><code>type</code></td>
    <td><code>1..1</code></td>
    <td>CodeableConcept</td>
    <td>Label for output</td>
<td>This MUST NOT be populated.</td>
</tr>
<tr>
  <td class="sub"><code>value[x]</code></td>
    <td><code>1..1</code></td>
    <td><a href="http://hl7.org/fhir/STU3/datatypes.html#open">*</a></td>
    <td>Result of output</td>
<td>This MUST NOT be populated.</td>
</tr>
</table>


## Task: Element Guidance ##

### note ###

If notes are made about a Task they MUST be displayed by the Encounter Report Receiving System (ERR).