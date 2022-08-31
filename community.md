---
title: Community
permalink: /community/
---

RealEstateCore is developed as an open source project by a community of developers, as part of their employments within academia, industry, consultancy, etc., and in their spare time. We happily accept contributions to the project, see contribution guide below. We're also happy to take questions, comments, requests, etc., via either our [GitHub repository's issues list](https://github.com/RealEstateCore/rec/issues), or via the [Gitter chat channel](https://gitter.im/RealEstateCore/community). Come in and say hi! Note that feature requests are implemented contingent on the availability and prioritization of the dev team, so we can make no guarantees -- the best way is thus to contribute missing bits yourself -- again, see section below.

Formally, the RealEstateCore project is organized as a non-profit consortium based in Stockholm, Sweden. Membership in the consortium is free, but corporate membership is associated with a cost (see details on our [main website](https://www.realestatecore.io/)). Those fees help fund outreach activities like conferences, web development, travel costs for devs to meetings, etc. Sitting on a committee or in the board of the project requires such membership (again, *free* for individuals), but contributing code and participating in the community is 100 % open to all, members or not.

## Technical Committee

The project Technical Committee (TC), elected by the project board, consists of leading developers in the community. TC works with development roadmap, open issues, merging of PRs, etc., and meets formally on monthly basis. At the time of writing, the TC consists of:

* Karl Hammar (Hammar Consulting) - chair
* Joakim Eriksson (RISE)
* Peter Hartlev (Cervum AB)
* Per Karlberg (Idun Real Estate Solutions)
* Erik Wallin (Idun Real Estate Solutions)

## Contributing

Before submitting contributions, it is most helpful to check in with the community to make sure no one else is working on the same problem. The same holds if you are askign a question or reporting a bug -- please conduct a brief search to see if someone has asked your question already; if they have, feel free to jump into the conversation. Otherwise, please [file a new issue](https://github.com/RealEstateCore/rec/issues) or [post to the chat](https://gitter.im/RealEstateCore/community).

If you wish to contribute, please note also:

* RealEstateCore uses the [BSD license](https://opensource.org/licenses/BSD-3-Clause). By contributing to RealEstateCore you recognize that any contributions will be assigned this same license.
* We reuse the [Brick Schema](https://brickschema.org/) Point and Equipment hierarchy; if your contributions concern these parts of the model hierarchy, we ask that you please direct them toward the upstream Brick Schema project instead. Once they are merged there, we can incorporate them when updating our dependencies to the latest Brick release.
* We deliver both DTDL and SHACL versions of RealEstateCore. We focus development efforts on the DTDL models, and generate SHACL models via translation (by hand or automation); contributions to the DTDL models are easier for us to work with, pull requests targeting the SHACL models may require more effort to integrate.

#### Bug reports

Bug reports are most helpful when they fully explain the problem and include as many details as possible.
Some suggestions:

- **Use a clear and descriptive title** for the issue that identifies the problem
- **Include as many details as possible** about the problem, including any relevant queries, datasets/data fragments, code, etc
- **Describe the observed and expected behavior**: for example, what query did you run, what were the results, and what did you expect the results to be? What definition exists and what definition would you expect?
- **Make sure you are using the most recent version of the REC repository**

#### Feature proposals and pull requests

Effective feature proposals/requests should fully explain the motivation and scope of the proposed changes, and should have at least an initial impression of the nature of the implementation.
The more detail, the better!

Changes are submitted through [Pull Requests](https://github.com/RealEstateCore/rec/pulls). . It is recommended that you become familiar with how to [fork a repository](https://help.github.com/en/articles/fork-a-repo) and [create a pull request](https://help.github.com/en/articles/creating-a-pull-request-from-a-fork).

