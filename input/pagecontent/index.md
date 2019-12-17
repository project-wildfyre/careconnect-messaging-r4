
### Introduction

The aim of this Implementation Guide is to *suggest* the minimal/recommended messaging capabilities of a clinical system so that it **forms part of LHCR and/or Hospital ecosystem**.

For FHIR this guide builds on the conformance resources in [INTEROPen Care Connect STU3 Implementation Guide](https://interopen.github.io/careconnect-base-stu3/) 

This IG does not describe an OPEN API (RESTful API). This can be found here: [Care Conect API](https://kevinmayfield.github.io/careconnect-api-stu3/)

### Inbound Messaging API

#### HL7v2

[HSCIC HL7v2](downloads/HSCIC ITK HL7 V2 Message Specifications.pdf) pipe+hat format **MUST** be supported. In particular the following Messaging Subsets are to considered the minimum requirement.

* 3.1.4 Patient Identity Management
* 3.1.1 Basic Inpatient / Outpatient Encounter Management

This is in order to support syncronisation with the Hospital Patient Administration Systems or LHCR Master Patient Index (MPI)

#### FHIR Messaging

This **SHOULD** be supported although we currently have no FHIR messaging standard in the UK/CareConnect. The recommendation would be to follow the [US Da Vinci Alerts](http://build.fhir.org/ig/HL7/davinci-alerts/) project and the FHIR Message definitions in this IG will be based on this.

### Outbound Messaging API

#### HL7v2

Support for HL7v2 will depend on system type. For Patient Administration Systems and Master Patient Index, the following **MUST** be supported (conversion to HSCIC standards may occur in the Trust Integration Engine).

* 3.1.4 Patient Identity Management
* 3.1.1 Basic Inpatient / Outpatient Encounter Management

For clinical systems such as EPR, the minimal requirement **SHOULD** include support for (**ALL clinical** encounters)

* 4.6 ADT^A04^ADT_A01 Register Outpatient

Dependent on the type of clinical information being created consideration should be given to the support of [ORU^R01](http://www.hl7.eu/refactored/msgORU_R01.html) message.

#### FHIR Messaging

This **SHOULD** be supported although we currently have no FHIR messaging standard in the UK/CareConnect. The recommendation would be to follow the [US Da Vinci Alerts](http://build.fhir.org/ig/HL7/davinci-alerts/) project and the FHIR Message definitions in this IG will be based on this.

For systems supporting child health data. Consideration should be given to supporting [NHS Digital Child Health Event Messages](https://nhsconnect.github.io/Digital-Child-Health-STU3/index.html).

### Outbound Document API

Many organisations and systems will require clinical information to be exchanged on document formats. The documents will most likely be in a unstrcutured format (PDF) with some systems requiring structured formats (FHIR Documents).

#### HL7v2 Messaging (Unstructured Documents)

Systems **SHOULD** support [MDM^T02](http://www.hl7.eu/refactored/msgMDM_T02.html) this should support metadata requirements of most systems and [IHE XDS](https://wiki.ihe.net/index.php/Cross-Enterprise_Document_Sharing)


#### FHIR Messaging (Unstrcutured Documents)

The emerging standard in a number of Local Health and Care Record Exemplars (LHCR) is the [IHE MHD format](https://build.fhir.org/ig/IHE/ITI.MHD), the recommendation is this **SHOULD** be followed.

#### FHIR Documents (Structured)

The NHS Digital Transfer of Care Initiative **MUST** be supported (when applicable) for the following letter types:

* [Inpatient and Day Case Discharge Summary Document](https://developer.nhs.uk/apis/itk3tocedischarge-2-6-0/) 
* [Emergency Care Discharge Summary Document](https://developer.nhs.uk/apis/itk3emergencycareedischarge-2-6-0/)
* [Inpatient and Day Case Discharge Summary (Mental Health)](https://developer.nhs.uk/apis/itk3tocmentalhealthedischarge-2-6-0/)
* [Outpatient Clinic Letter Document](https://developer.nhs.uk/apis/itk3tocoutpatientletter-2-6-0/)