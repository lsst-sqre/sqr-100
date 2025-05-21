# Contributing capabilities to data.lsst.cloud

```{abstract}
Rubin makes extensive use of the Rubin Science Platform and the deployment infrastructure (phalanx) that it relies on. While there are over a dozen deployments of the RSP, the production instance serving Rubin data rights holders at data.lsst.cloud has the highest bar in terms of reliability, scalability and documentation.

This technote describes the procedure and requirements for adding capabilities exposed to data.lsst.cloud users specifically.
```

## Context

In the context of this document, a Phalanx application (service) can be:

* **First party**: A service developed and/or deployed and supported by Rubin Data Services.

* **Second party**: A service developed and/or deployed and supported by non-RDS Rubin developers/teams

* **Third party**: A service developed and/or deployed and supported outside of Rubin Observatory.

Many teams have found Phalanx to be an effective deployment infrastructure for their service, and many applications have been added in specific contexts (summit, staff RSP at USDF, etc).
By intent we are relatively permissive in accepting additional applications provided their developers have enough experience engineering Kubernetes services that they can self-serve without adding a support burden to Data Services.

For obvious reasons, there is a significantly higher bar for including in the cloud-based deployment at data.lsst.cloud, which serves the Rubin scientific community.
These include criteria in the areas of:

* reliability
* scalability
* operability
* security
* support
* documentation
* cost

This technote describes the criteria and requirements for inclusion of an application in the data.lsst.cloud environment.
It does not cover the policies for deploying updates of these applications, which are covered in [SQR-056](https://sqr-056.lsst.io)

Unless explicitly stated, the content of this technote applies equally to second and third party applications, the same as it does for first-party services.
This document is likely to evolve with additional operational experience with contributed software and services.

## Criteria for inclusion

The following sub-sections list requirements for being included and staying included as a data.lsst.cloud capability.

### Usefulness

Every included package or application increases platform complexity, adds to the support burden, and increases the surface attack for security and reputational risk.
Accepting contributions involves a trade-off between the above factors and how useful something is to how many people.

* **U1**: All first-part contributions are approved by the Rubin Data Services lead in conjunction, where appropriate, with the Rubin Science Platform product owners. Second and third part contributions have to be approved by the AD of Data Management and the AD of System Performance or their designates.

### Technical requirements

* **T1**: All technical criteria for inclusion in the RSP builds and/or Phalanx applications are necessary (but not sufficient)

* **T2**: Services need to be accompanied by a notebook for scale-testing. Services have to be successfully scale and reliability tested to the load specified by Data Services (which will vary depending on the characteristics and anticipated usage). Application code has to be equally tested for memory consumption etc.

* **T3**: All code has to be open-source and hosted on Github, as per Rubin Data Management policy.

### Operational Requirements

* **O1**: A security review is required. Note this should not be relied on in lieu of software engineering best practices for creating secure applications

* **O2**: All services need to provide an authentication method. Unless special dispensation has been granted by the Rubin Data Services lead, this is to mean that services have to be authenticated with gafaelfawr

* **O3**: All contributions need to provide a "check-out" monitoring notebook. For services this should include a live-ness test, for application code this should require a functional test.

* **O4**: Contributed applications have to be able to data.lsst.cloud's "raze to the ground and re-deploy" security response. This means that the service needs to be entirely reconstituted from configuration deployment and back-ups.

* **O5**: Contributors have to agree on a back-up strategy with the Rubin Data Services lead.

* **O6**: At least two persons have to be listed as maintainers of the contribution. For services, at least one of them must be willing to provide support to the same best basis as first-party services (technote in preparation)

* **07**: PRs opened the service initiated by Rubin Data Services engineers or their systems (eg renovate) need to be serviced in a reasonable amount of time

* **08**: All services and code need to follow the appropriate policies for updates (eg Path Thursday roll-outs, inclusion in Recommended builds, etc)


### Documentation

* **D1**: A technote in the delivery note format (template to be provided) will accompany each inclusion. This will include a disaster recovery plan.

* **D2**: The Community Science Team Lead can require user-facing documentation to their standard

* **D3**: A notebook that runs on data.lsst.cloud should demonstrate the major features of the capability for inclusion in system-test for any callable API, software package or other payload that can be so addressed.


## Other policies

### Exclusion

If there are persistent issues with keeping a service compliant with the criteria in this document, the application will be removed from data.lsst.cloud on the approval of the AD for Data Management.

### Additional requirements for second-party and third-party contributions

The Rubin Data Services lead, who also serves as the software release manager for data.lsst.cloud, has to sign off that the criteria for this document have been met

### Additional requirements for third-party contributions only

Third-party contributions need to be accompanied by an MOU signed by the Associate Director of Data Management and an appropriate counterpart from the contributing organisation formalising agreement to comply with the content of this document.
