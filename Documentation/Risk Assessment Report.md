# SOHO Network Simulation – Risk Assessment Report

## Project Context

This assessment identifies and evaluates potential risks associated with the **SOHO Network Simulation** project.

The network includes virtualized Windows and Linux machines, a file/backup server, and Windows Firewall configurations to simulate VLANs, access control, and security measures within a small business environment.

## 1. Objective

To analyze technical and operational risks that may impact network performance, data integrity, or security, and to recommend mitigation strategies to ensure system reliability and business continuity.

## 2. Identified Risks and Mitigation Strategies

| Risk Category | Description | Impact | Likelihood | Mitigation Strategy |
|---------------|-------------|--------|------------|---------------------|
| **1. Firewall Misconfiguration** | Incorrect or incomplete firewall rules may allow unauthorized access from guest systems or block legitimate internal communication. | **High** | **Medium** | Implement a firewall change log, test all rules post-configuration, and perform periodic reviews using simulated attacks to confirm isolation and protection. |
| **2. Backup Failure or Data Loss** | Backups may fail due to misconfigured schedules, storage limits, or hardware failure, leading to potential data loss. | **High** | **Medium** | Use RAID1 redundancy, schedule automated daily backups, store copies offsite or in the cloud, and verify integrity of backup files weekly. |
| **3. Virtual Machine Resource Exhaustion** | The host system may not have sufficient CPU, RAM, or disk space to handle multiple VMs simultaneously, affecting performance. | **Medium** | **High** | Allocate minimum required resources to each VM, monitor host utilization, and scale up hardware or migrate workloads to cloud infrastructure if demand increases. |
| **4. Data Corruption or Retention Gaps** | Backup retention periods may overlap or delete data prematurely before integrity verification. | **Medium** | **Medium** | Implement a 30-day rolling backup policy, verify each backup's integrity before rotation, and maintain redundant copies on external storage. |
| **5. Unauthorized Network Access (Internal Threats)** | Internal users could gain elevated access to restricted data through weak credentials or shared accounts. | **High** | **Low** | Apply strong password policies, role-based access control, and monitor login attempts through Windows Event Viewer or network monitoring tools. |
| **6. Hardware Failure (NAS / Router)** | Physical failure of NAS drives or router hardware could lead to downtime or partial data loss. | **High** | **Low** | Maintain spare hardware, enable SMART monitoring for drives, and configure RAID mirroring with tested recovery procedures. |
| **7. Firewall Limitations / Outdated Rules** | Static rules may become obsolete as systems evolve, creating security gaps. | **Medium** | **Medium** | Review and update firewall configurations quarterly, ensuring compatibility with new applications and user requirements. |
| **8. Misconfigured VLAN Simulation** | Incorrect network segmentation may fail to isolate guest and staff traffic. | **Medium** | **Low** | Validate VLAN simulations through ping and SMB access tests; maintain clear IP documentation for all subnets. |
| **9. Malware Infection (Test Environment)** | Virtual test systems may be exposed to unsafe software during experimentation. | **Medium** | **Low** | Run VMs in isolated internal networks, keep snapshots before tests, and ensure antivirus protection is active on the host system. |

## 3. Risk Impact Summary

| Impact Level | Description |
|--------------|-------------|
| High | Could cause system downtime, data loss, or security compromise. |
| Medium | May degrade performance or reduce reliability without full system failure. |
| Low | Minimal effect on functionality; easily reversible through standard maintenance. |

## 4. Recommendations

1. **Automate monitoring:** Use Windows Event Viewer and NAS monitoring tools for proactive alerts.
2. **Enforce documentation:** Maintain a configuration log for firewall rules, IP addressing, and backups.
3. **Perform quarterly audits:** Review access controls, VLAN isolation, and patch levels.
4. **Test disaster recovery:** Simulate system failures to confirm that backups and snapshots can fully restore services.
5. **Scale strategically:** Reassess hardware resources if VM usage or staff count increases.

## 5. Conclusion

The SOHO network simulation demonstrates effective implementation of small-scale enterprise security principles.

While risks such as firewall misconfiguration and backup failure pose significant threats, they can be mitigated through **regular testing**, **documentation**, **redundancy**, **and proactive maintenance**.

The system, as designed, provides a strong foundation for secure, scalable IT operations within a limited budget.
