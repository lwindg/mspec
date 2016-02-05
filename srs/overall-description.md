# Overall Description

## Product Perspective
_<font color="gray">
&lt;Describe the context and origin of the product being specified in this SRS. For example, state whether this product is a follow-on member of a product family, a replacement for certain existing systems, or a new, self-contained product. If the SRS defines a component of a larger system, relate the requirements of the larger system to the functionality of this software and identify interfaces between the two. A simple diagram that shows the major components of the overall system, subsystem interconnections, and external interfaces can be helpful.&gt;
</font>_

Only UC-8100-LX-CG family is included currently. Below are the supported model and system specification:

| CG Model Name | Ref Std.Model | Firmware Base Version | CPU    | SDRAM | mSD | SD  |
| ------------- | ------------- | --------------------- | ------ | ----- | --- | --- |
| UC-8112-LX-CG | UC-8112-LX-CG | V1.0                  | 1GHz   | 512MB | 2GB | 4GB |
| UC-8132-LX-CG | UC-8132-LX-CG | V1.0                  | 300MHz | 256MB | -   | 4GB |

## User Classes and Characteristics
_<font color="gray">
&lt;Identify the various user classes that you anticipate will use this product. User classes may be differentiated based on frequency of use, subset of product functions used, technical expertise, security or privilege levels, educational level, or experience. Describe the pertinent characteristics of each user class. Certain requirements may pertain only to certain user classes. Distinguish the favored user classes from those who are less important to satisfy.&gt;
</font>_

System integrator and field operator could be involved in this software operation.

## Operating Environment
_<font color="gray">
&lt;Describe the environment in which the software will operate, including the hardware platform, operating system and versions, and any other software components or applications with which it must peacefully coexist.&gt;
</font>_

The platform of UC-8100-LX-CG should follow standard model UC-8100-LX, an embedded computer with Linux operating system and Debian 7 software package installed is required.

When the kernel of standard model is upgraded, for example, security patch release or bugs fix, the UC-8100-LX-CG kernel should also be patched in the next release.

## Design and Implementation Constraints
_<font color="gray">
&lt;Describe any items or issues that will limit the options available to the developers. These might include: corporate or regulatory policies; hardware limitations (timing requirements, memory requirements); interfaces to other applications; specific technologies, tools, and databases to be used; parallel operations; language requirements; communications protocols; security considerations; design conventions or programming standards (for example, if the customer’s organization will be responsible for maintaining the delivered software).&gt;
</font>_

In the 2'nd phase, this software is targeting ONLY on UC-8100 standard model and focus on celullar router.

Some of the spec of UC-8100 standard model will limit the design, for example, without EEPROM, the implementation of software lock feature will change from one platform to another and will not be reliable enough.

## User Documentation
_<font color="gray">
&lt;List the user documentation components (such as user manuals, on-line help, and tutorials) that will be delivered along with the software. Identify any known user documentation delivery formats or standards.&gt;
</font>_

CG's user's manual includes WEB operation is required.

## Assumptions and Dependencies

_<font color="gray">
&lt;List any assumed factors (as opposed to known facts) that could affect the requirements stated in the SRS. These could include third-party or commercial components that you plan to use, issues around the development or operating environment, or constraints. The project could be affected if these assumptions are incorrect, are not shared, or change. Also identify any dependencies the project has on external factors, such as software components that you intend to reuse from another project, unless they are already documented elsewhere (for example, in the vision and scope document or the project plan).&gt;
</font>_

This state of this SRS is based on the system requirement and the specification of UC-8100 standard model.

