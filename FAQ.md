# Frequently Asked Questions (FAQ)

Welcome to the **CDEvents FAQ**! This page provides answers to common questions about CDEvents. Whether you're new to CDEvents or looking to deepen your understanding, you'll find valuable information here. If you don't find the answer you're looking for, please refer to our [documentation](https://cdevents.dev/docs/), [whitepaper](https://cdevents.dev/docs/wpaper/), or explore relevant discussions on [GitHub](https://github.com/cdevents).

---

## Table of Contents

1. [General Questions](#general-questions)
2. [Technical Questions](#technical-questions)
3. [Implementation and Integration](#implementation-and-integration)
4. [Security and Compliance](#security-and-compliance)
5. [Community and Support](#community-and-support)
6. [Contributing](#contributing)
7. [Miscellaneous](#miscellaneous)

---

## General Questions

### **Q: What is CDEvents?**
**A:** CDEvents is an open specification for Continuous Delivery events, designed to promote interoperability between tools in the software production ecosystem. It standardizes the format of events across various phases of the software development lifecycle, enabling seamless communication and integration between different CI/CD tools.

---

### **Q: Why was CDEvents created?**
**A:** CDEvents was created to address the fragmentation in the Continuous Delivery (CD) toolchain. By providing a common event specification, it allows different tools and platforms to communicate more effectively, reducing integration complexity and preventing vendor lock-in. This fosters a more flexible and adaptable CD pipeline.

---

### **Q: Who is behind CDEvents?**
**A:** CDEvents is developed and maintained by a collaborative working group comprising industry experts, open-source contributors, and representatives from various organizations committed to enhancing Continuous Delivery practices.

---

### **Q: How does CDEvents differ from other event specifications?**
**A:** Unlike proprietary event formats or tool-specific integrations, CDEvents is an open, vendor-neutral specification focused solely on Continuous Delivery events. It emphasizes interoperability, flexibility, and ease of adoption across diverse toolchains and environments.

---

## Technical Questions

### **Q: How does CDEvents ensure event consistency across tools?**
**A:** CDEvents provides a standardized event schema that all compliant tools must follow. This includes consistent naming conventions, required fields, and data formats. By adhering to this schema, events emitted by different tools maintain uniformity, simplifying integration and processing.

---

### **Q: What event types are defined by CDEvents?**
**A:** CDEvents defines a variety of event types covering different stages of the CD pipeline, including but not limited to:
- **Build Events:** Indicate the start, success, or failure of a build process.
- **Test Events:** Capture test execution details and results.
- **Deploy Events:** Represent deployment actions, including initiation and completion.
- **Pipeline Events:** Provide insights into the overall workflow and pipeline status.
- **Approval Events:** Handle manual approval steps within the pipeline.
- **Artifact Events:** Manage artifact creation, storage, and retrieval.

For a comprehensive list, refer to the [CDEvents specification](https://github.com/cdevents/spec/blob/main/spec.md).

---

### **Q: What technologies does CDEvents use?**
**A:** CDEvents is technology-agnostic and can be implemented using various protocols and data formats. Common implementations use JSON for event payloads and can be transported over HTTP, WebSockets, or message brokers like Kafka and RabbitMQ.

---

### **Q: Are there any libraries or SDKs available for CDEvents?**
**A:** Yes, the community has developed several libraries and SDKs in various programming languages to facilitate the implementation of CDEvents. Below are some of the available SDKs:

- [Go SDK](https://github.com/cdevents/sdk-go)
- [Java SDK](https://github.com/cdevents/sdk-java)
- [Rust SDK](https://github.com/cdevents/sdk-rust)

More SDKs are being developed, and contributions are welcome! You can find additional resources in our [GitHub repositories](https://github.com/cdevents/spec) or in the [official documentation](https://cdevents.dev/docs/).

---

### **Q: How do CDEvents handle event metadata?**
**A:** CDEvents includes a metadata section in each event payload, containing information such as event type, source, timestamp, and unique identifiers. This metadata ensures that events can be properly tracked, filtered, and processed across different tools and systems. You can learn more about the context and metadata in the [CDEvent Context section](https://github.com/cdevents/spec/blob/main/spec.md#cdevent-context) of the specification.

---

## Implementation and Integration

### **Q: How do I implement CDEvents in my CI/CD pipeline?**
**A:** Implementing CDEvents involves several key steps, and while a definitive answer is still being discussed by the community's working group, the following points provide a good starting framework:

1. **Identify Integration Points:** Determine where events are generated and consumed in your pipeline.
2. **Adopt the CDEvents Schema:** Ensure that your tools emit and listen to events following the CDEvents specification.
3. **Use Existing Libraries:** Leverage available SDKs or libraries to simplify implementation.
4. **Configure Event Transport:** Set up the communication mechanism (e.g., HTTP, message broker) for event transmission.
5. **Test Integration:** Validate that events are correctly emitted, received, and processed across your tools.

We encourage you to follow the discussions and contributions from the [CDEvents Implementation Working Group](https://github.com/cdevents/implementation-wg) as they continue to refine the best practices for implementation. Meanwhile, you can refer to our [implementation guide](https://cdevents.dev/docs/) for detailed steps and examples.

---

### **Q: Can CDEvents be integrated with popular CI/CD tools like Jenkins, GitLab CI, or GitHub Actions?**
**A:** Yes, CDEvents is designed to be tool-agnostic and can integrate with popular CI/CD tools. Integration can be achieved by configuring these tools to emit and consume CDEvents-compliant events. Some community-contributed plugins and extensions may already exist to facilitate this integration. For example, check out the CDEvents plugin for [Jenkins](https://plugins.jenkins.io/cdevents/).

Other tools like [Spinnaker](https://spinnaker.io/), [Testkube](https://testkube.io/), and [Guac.sh](https://guac.sh/) are also integrating CDEvents. You can visit the [CDEvents homepage](https://cdevents.dev) for a full list of supported tools and their logos, as well as resources on how to get started with each.

---

### **Q: What are the best practices for implementing CDEvents?**
**A:** Best practices for implementing CDEvents include:

- **Adhere to the Specification:** Ensure that all events conform to the CDEvents schema to maintain compatibility and consistency.
- **Leverage Versioning Built Into the Spec:** CDEvents and their schemas are versioned, so ensure your implementation follows the appropriate event versions for backward and forward compatibility.
- **Secure Event Transport:** CDEvents rely on the underlying transport protocol (e.g., HTTP, message broker), where encryption mechanisms like TLS can be used to secure event transmission.
- **Include Links for Sensitive Data:** To keep events lean and secure, CDEvents includes links to additional data rather than embedding it directly. These links can be protected by authentication where necessary.
- **Verify Event Integrity:** In some use cases, event consumers may need to verify the authenticity and integrity of events. This can be achieved by relying on the underlying protocol’s facilities for tamper-proof event verification, a feature that is being actively worked on in collaboration with the CloudEvents community.
- **Validate Events:** Use schema validation to ensure that events follow the CDEvents specification and maintain integrity across systems.
- **Monitor and Log Events:** Maintain visibility into the event flow by logging and monitoring events, helping with troubleshooting and auditing.
- **Document Your Implementation:** Clearly document your event workflows and integration for future maintainability and team collaboration.

For more detailed best practices, visit our [implementation best practices](https://cdevents.dev).

---

## Security and Compliance

### **Q: How does CDEvents handle authentication and authorization?**
**A:** CDEvents is a specification and does not prescribe specific authentication or authorization mechanisms. Instead, it relies on the underlying transport protocols (e.g., HTTPS, message brokers) to secure event transmission. To keep events lean, CDEvents typically includes links to external resources rather than embedding sensitive data directly in the events. These external resources can be protected by authentication and authorization mechanisms (e.g., OAuth, API keys) as needed in your specific implementation.

In some scenarios, it may also be necessary to verify the integrity and origin of events. This verification depends on the capabilities of the underlying transport protocol, and the community is actively collaborating with CloudEvents to explore mechanisms for event integrity verification.

---

### **Q: Does CDEvents support encryption of event data?**
**A:** CDEvents itself does not define encryption standards. Whether or not to encrypt event data depends on the specific use case. In cases where sensitive data is involved, it may be necessary to use encryption during transmission or at rest. CDEvents relies on the underlying transport protocol (e.g., HTTPS, message brokers) to provide encryption where needed. The choice of encryption methods will depend on the transport and storage solutions used in your implementation.

---

### **Q: How does CDEvents ensure compliance with data protection regulations like GDPR?**
**A:** CDEvents promotes best practices for data handling, such as minimizing the inclusion of sensitive data in event payloads. However, compliance with regulations like GDPR depends on how CDEvents is implemented within your organization. Ensure that your event handling processes adhere to relevant data protection laws by implementing necessary safeguards, such as data anonymization and access controls.

---

### **Q: Can CDEvents be used in regulated industries?**
**A:** Yes, CDEvents can be utilized in regulated industries provided that implementations comply with industry-specific regulations and standards. This includes ensuring data privacy, maintaining audit trails, and adhering to security protocols as required by the respective regulatory frameworks.

---

## Community and Support

### **Q: How can I get involved in the CDEvents community?**
**A:** You can participate in the CDEvents community by:
- **Joining Our Slack Channel:** Engage with other members and contributors.
- **Attending Working Group Meetings:** Participate in discussions and decision-making.
- **Contributing to GitHub:** Submit issues, propose enhancements, or contribute code.
- **Participating in Events:** Attend webinars, workshops, and conferences related to CDEvents.

Visit our [community page](https://cdevents.dev/community/) for more information on how to get involved.

---

### **Q: Where can I find support if I encounter issues with CDEvents?**
**A:** Support is available through several channels:
- **GitHub Issues:** Report bugs or request features via our [GitHub issues tracker](https://github.com/cdevents/spec/issues).
- **Slack Channel:** Join our [Slack workspace](https://cdeliveryfdn.slack.com/join/shared_invite/zt-nwc0jjd0-G65oEpv5ynFfPD5oOX5Ogg#/shared-invite/email) for real-time assistance and discussions.
- **Community Forums:** Participate in discussions on our [community forums](https://cdevents.dev/community/).
- **Documentation:** Refer to our comprehensive [documentation](https://cdevents.dev/docs/) for guides and troubleshooting tips.

---

### **Q: Are there any official CDEvents tutorials or training materials?**
**A:** Yes, we offer a variety of tutorials and training resources, including:
- **Step-by-Step Guides:** Detailed guides available in our [documentation](https://cdevents.dev/docs/).
- **Video Tutorials:** Instructional videos on our [YouTube channel](https://www.youtube.com/channel/UC7HcWhSetq6nTlpMXPHKz_A).
- **Webinars and Workshops:** Regularly scheduled sessions for in-depth learning.
- **Sample Projects:** Example implementations on our [GitHub repositories](https://github.com/cdevents/implementation-wg).

---

### **Q: How can I stay updated with the latest CDEvents news and updates?**
**A:** Stay informed by:
- **Subscribing to Our Newsletter:** Receive updates directly to your inbox.
- **Following on Social Media:** Follow our [Twitter](https://x.com/CDeliveryFdn) and [LinkedIn](https://www.linkedin.com/company/cdeliveryfdn) profiles.
- **Monitoring GitHub:** Watch our [GitHub repository](https://github.com/cdfoundation) for releases and announcements.
- **Joining Community Channels:** Engage with the community through Slack and forums.

---

## Contributing

### **Q: How can I contribute to the CDEvents specification?**
**A:** Contributions are welcome! You can contribute by:
- **Submitting Proposals:** Open a [GitHub issue](https://github.com/cdevents/spec/issues) to propose new features or changes.
- **Opening Pull Requests:** Directly submit pull requests with your proposed changes.
- **Participating in Discussions:** Join working group meetings and discussions to provide feedback and suggestions.
- **Contributing to Documentation:** Help improve our [documentation](https://cdevents.dev/) by adding tutorials, examples, or clarifications.

Refer to our [contribution guidelines](https://github.com/cdevents/.github/blob/main/docs/CONTRIBUTING.md) for detailed instructions.

---

### **Q: What is the process for proposing a new event type?**
**A:** To propose a new event type:
1. **Create a GitHub Issue:** Describe the proposed event type, including its purpose and use cases.
2. **Draft the Specification:** Provide a detailed specification for the event, following the existing schema structure.
3. **Review and Feedback:** Engage with the community and maintainers for feedback and revisions.
4. **Approval and Integration:** Once approved, the event type will be integrated into the CDEvents specification.

---

### **Q: Are there opportunities for sponsorship or funding contributions?**
**A:** Yes, we welcome sponsorships and funding contributions to support the ongoing development and maintenance of CDEvents. Interested parties can reach out through our [sponsorship page](https://cd.foundation/) for more information on how to contribute financially.

---

## Miscellaneous

### **Q: Can CDEvents be used outside of Continuous Delivery?**
**A:** Yes, CDEvents is designed to cover a broad range of scenarios across the software development lifecycle, not just Continuous Delivery. In addition to CD, CDEvents also supports Continuous Integration, DevOps practices, and IT operations workflows. The specification defines events that span from issue tracking and source code management (SCM) to CI/CD processes, deployments, and even monitoring and observability. For more details on Continuous Delivery, refer to the [CD Foundation FAQ](https://github.com/cdfoundation/faq?tab=readme-ov-file#what-is-continuous-delivery-cd).

---

### **Q: Is there a roadmap for the future development of CDEvents?**
**A:** Yes, CDEvents maintains a roadmap that outlines planned features, enhancements, and milestones. You can view the current roadmap in our [GitHub milestones](https://github.com/cdevents/spec/milestones) and participate in shaping future developments by contributing to discussions and proposals.

---

### **Q: How does CDEvents handle backward compatibility?**
**A:** Maintaining backward compatibility is important for CDEvents. When introducing changes:
- **Minor Updates:** New fields or event types may be added without breaking existing structures, ensuring that current integrations continue to work.
- **Major Updates:** Breaking changes may occur, especially before reaching version 1.0, and will be communicated clearly to users with guidance for migration.
- **Versioning Before 1.0:** Until we reach version 1.0, breaking changes may be introduced as the specification evolves. Users should be prepared for potential changes during this period.

For more details, see the [versioning and compatibility section](https://cdevents.dev/docs/primer/#versioning) of our documentation.

---

### **Q: Are there any limitations or known issues with CDEvents?**
**A:** As with any specification, CDEvents has its limitations and ongoing areas of improvement. Current known issues and limitations are tracked in our [GitHub issues tracker](https://github.com/cdevents/spec/issues). We encourage users to report any issues they encounter and participate in discussions to help address them.

---

### **Q: How does CDEvents handle large-scale event processing?**
**A:** CDEvents is designed with scalability in mind. Key features that support large-scale event processing include:
- **Compact Event Design:** Events are kept as small as possible to minimize overhead and improve performance.
- **Efficient Routing and Filtering:** The event context includes fields (such as `subject`) that can be used to efficiently route and filter events without parsing the entire payload. These fields are also available at the CloudEvents level, enabling even more efficient processing.
- **Efficient Workflow Search:** CDEvents includes links to help efficiently search and retrieve events that belong to a specific workflow, supporting the storage and querying of large volumes of events.
  
While CDEvents provides the foundation for scalability, implementers should ensure their infrastructure (e.g., message brokers, databases) is capable of handling the expected event load based on their specific use case.

---

### **Q: Are there any case studies or success stories using CDEvents?**
**A:** 
1. **Fidelity Investments**: The CDEvents project is key to enabling interoperability, which simplifies the Software Delivery Lifecycle (SDL) processes. Fidelity uses an event-driven architecture to achieve continuous compliance for apps delivered in a highly regulated environment. Their internal tool, the Fidelity Pipeline Library, offers reusable pipeline templates with event triggers, showcasing how CDEvents can enhance developer experience and feature velocity.

2. **Ericsson**: Ericsson co-founded CDEvents to address the need for innovative and simplified software deployment in telecommunications. They have implemented CDEvents in their CI/CD pipelines, demonstrating its effectiveness in achieving interoperability and streamlining processes.

3. **TestKube**: This Kubernetes-native testing framework has adopted CDEvents to improve feedback loops and quality-gated workflows within CI/CD pipelines. The integration of test events allows for better tracking and management of testing activities.

For more detailed insights into these case studies and others related to CDEvents, you can visit the following links:

- [CDEvents Adoption - CD Foundation](https://cd.foundation/blog/2023/05/08/cdevents-real-world-adoption/) 
- [OpenTelemetry Inspires CDF's Event-Driven Architecture Plan](https://www.techtarget.com/searchitoperations/news/252521316/OpenTelemetry-inspires-CDFs-event-driven-architecture-plan) 


---

This FAQ aims to address a wide range of questions about CDEvents, from general concepts to technical implementations and community involvement. We continuously update this page based on community feedback and evolving best practices. If you have additional questions or suggestions, please reach out or engage with us through our [community channels](https://cdevents.dev/community/).

---

**Happy Continuous Delivering with CDEvents! 🚀**
