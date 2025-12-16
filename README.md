# Zero Trust for the AI Era: Securing Today's Cloud with Microsoft's Well-Architected Principles

[![Session Level](https://img.shields.io/badge/Level-400%20(Expert)-red)](https://learn.microsoft.com)
[![Duration](https://img.shields.io/badge/Duration-2%20Hours-blue)](https://learn.microsoft.com)
[![Azure](https://img.shields.io/badge/Platform-Microsoft%20Azure-0078D4?logo=microsoft-azure)](https://azure.microsoft.com)

## 🎯 Session Overview

This Level 400 expert session focuses on applying Microsoft's Zero Trust model to the Security pillar of the Azure Well-Architected Framework, with special emphasis on securing AI workloads. Attendees will learn how to implement the three core Zero Trust principles—**Verify Explicitly**, **Use Least Privilege Access**, and **Assume Breach**—within modern cloud environments that increasingly integrate AI services like Azure AI Foundry, Microsoft Copilot, and Azure OpenAI.

### Key Focus Areas

| Area | Description | WAF Pillar Alignment |
|------|-------------|---------------------|
| **Identity Protection** | Entra ID, Conditional Access, PIM for AI workloads | Security, Identity |
| **Data Governance** | Microsoft Purview, DLP, Data Classification for AI data flows | Security, Data |
| **Workload Isolation** | Network segmentation, private endpoints, NSGs for AI services | Security, Networking |

## 📚 Session Agenda (2 Hours)

| Time | Topic | Type |
|------|-------|------|
| 0:00-0:15 | Zero Trust Foundations & AI Landscape | Presentation |
| 0:15-0:30 | Well-Architected Framework Security Pillar Deep Dive | Presentation |
| 0:30-0:50 | **Lab 1**: Identity Protection - Before & After Zero Trust | Hands-on |
| 0:50-1:00 | Break | - |
| 1:00-1:15 | Data Governance for AI Workloads | Presentation |
| 1:15-1:35 | **Lab 2**: Data Governance - Securing AI Data Flows | Hands-on |
| 1:35-1:50 | **Lab 3**: Workload Isolation - Network Segmentation | Hands-on |
| 1:50-2:00 | Summary & Q&A | Discussion |

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          ZERO TRUST ARCHITECTURE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐                      │
│  │   IDENTITY  │    │    DATA     │    │  NETWORK    │                      │
│  │   PILLAR    │    │   PILLAR    │    │   PILLAR    │                      │
│  ├─────────────┤    ├─────────────┤    ├─────────────┤                      │
│  │ • Entra ID  │    │ • Purview   │    │ • NSGs      │                      │
│  │ • MFA       │    │ • DLP       │    │ • Private   │                      │
│  │ • PIM       │    │ • Labels    │    │   Endpoints │                      │
│  │ • Cond.     │    │ • Rights    │    │ • Azure FW  │                      │
│  │   Access    │    │   Mgmt      │    │ • Bastion   │                      │
│  └──────┬──────┘    └──────┬──────┘    └──────┬──────┘                      │
│         │                  │                  │                              │
│         └──────────────────┼──────────────────┘                              │
│                            │                                                 │
│                   ┌────────▼────────┐                                       │
│                   │   AI WORKLOADS  │                                       │
│                   ├─────────────────┤                                       │
│                   │ • Azure AI      │                                       │
│                   │   Foundry       │                                       │
│                   │ • Azure OpenAI  │                                       │
│                   │ • Copilot       │                                       │
│                   │   Integration   │                                       │
│                   └─────────────────┘                                       │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

## 🔬 Hands-on Labs

### Lab 1: Identity Protection - Before & After Zero Trust
**Duration**: 20 minutes

Demonstrates the vulnerability of resources without proper identity controls and shows the remediation using Zero Trust principles.

**Before State** (Insecure):
- Basic authentication only
- No Conditional Access
- No MFA enforcement
- Service accounts with persistent admin rights

**After State** (Zero Trust):
- Phishing-resistant MFA
- Risk-based Conditional Access
- Just-in-Time access with PIM
- Managed Identities for AI services

### Lab 2: Data Governance - Securing AI Data Flows
**Duration**: 20 minutes

Shows how data flows through AI systems without proper classification and implements Microsoft Purview controls.

**Before State** (Insecure):
- No data classification
- AI models accessing all data equally
- No DLP policies
- Unrestricted data movement

**After State** (Zero Trust):
- Sensitivity labels applied
- AI access restricted by classification
- DLP policies blocking sensitive data exfiltration
- Information barriers for AI workloads

### Lab 3: Workload Isolation - Network Segmentation
**Duration**: 15 minutes

Demonstrates open network architecture vs. properly segmented Zero Trust network.

**Before State** (Insecure):
- Public endpoints exposed
- No network segmentation
- Direct internet access from AI services
- Flat network topology

**After State** (Zero Trust):
- Private endpoints only
- Network Security Groups
- Azure Firewall inspection
- Micro-segmentation

## 📁 Repository Structure

```
zero-trust-ai-session/
├── README.md                          # This file
├── presentation/
│   └── zero-trust-ai-session.pptx     # Main presentation deck
├── labs/
│   ├── lab1-identity/
│   │   ├── README.md                  # Lab 1 instructions
│   │   ├── deploy-insecure.ps1        # Deploy insecure state
│   │   ├── deploy-secure.ps1          # Apply Zero Trust controls
│   │   ├── verify-state.ps1           # Verify configuration
│   │   └── cleanup.ps1                # Clean up resources
│   ├── lab2-data-governance/
│   │   ├── README.md                  # Lab 2 instructions
│   │   ├── deploy-insecure.ps1        # Deploy without data governance
│   │   ├── deploy-secure.ps1          # Apply Purview/DLP controls
│   │   ├── test-dlp.ps1               # Test DLP policies
│   │   └── cleanup.ps1                # Clean up resources
│   └── lab3-workload-isolation/
│       ├── README.md                  # Lab 3 instructions
│       ├── deploy-insecure.ps1        # Deploy open network
│       ├── deploy-secure.ps1          # Apply network controls
│       ├── test-connectivity.ps1      # Test network isolation
│       └── cleanup.ps1                # Clean up resources
├── scripts/
│   ├── prereqs-check.ps1              # Verify prerequisites
│   ├── full-demo-deploy.ps1           # Deploy all labs
│   └── full-cleanup.ps1               # Clean up everything
├── docs/
│   ├── presenter-notes.md             # Speaker notes
│   ├── ai-agent-decision-tree.md      # AI solution guidance
│   └── waf-security-pillar.md         # WAF alignment
└── assets/
    └── diagrams/                      # Architecture diagrams
```

## ⚙️ Prerequisites

### Required Azure Resources
- Azure Subscription with Owner/Contributor access
- Microsoft Entra ID P2 license (for PIM and Identity Protection)
- Microsoft 365 E5 or Purview license (for data governance features)

### Required Tools
- [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli) (v2.50+)
- [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps) (v10.0+)
- [Visual Studio Code](https://code.visualstudio.com/)
- [GitHub CLI](https://cli.github.com/) (optional)

### Azure Services Used
| Service | Purpose |
|---------|---------|
| Azure AI Foundry | AI model deployment |
| Azure OpenAI | GPT model access |
| Microsoft Entra ID | Identity management |
| Microsoft Purview | Data governance |
| Azure Key Vault | Secrets management |
| Azure Virtual Network | Network isolation |
| Azure Private Link | Private connectivity |
| Azure Firewall | Network security |
| Azure Bastion | Secure management |

## 🚀 Quick Start

```powershell
# Clone the repository
git clone https://github.com/yourusername/zero-trust-ai-session.git
cd zero-trust-ai-session

# Verify prerequisites
./scripts/prereqs-check.ps1

# Deploy all labs (creates both insecure and secure states)
./scripts/full-demo-deploy.ps1 -SubscriptionId "<your-subscription-id>"

# Run individual lab
cd labs/lab1-identity
./deploy-insecure.ps1
# ... demonstrate vulnerability ...
./deploy-secure.ps1
# ... verify remediation ...
./verify-state.ps1

# Clean up when done
./scripts/full-cleanup.ps1
```

## 📖 Key Learning Outcomes

By the end of this session, attendees will be able to:

1. **Understand** the Zero Trust security model and its three core principles
2. **Apply** the Well-Architected Framework Security pillar to AI workloads
3. **Implement** identity protection using Entra ID and Conditional Access
4. **Configure** data governance with Microsoft Purview for AI data flows
5. **Design** network architectures with proper workload isolation
6. **Evaluate** AI solution options using Microsoft's decision framework
7. **Demonstrate** before/after states showing Zero Trust remediation

## 🔗 Key References

### Microsoft Documentation
- [Zero Trust Deployment Guide](https://learn.microsoft.com/security/zero-trust/deploy/)
- [Well-Architected Framework Security Pillar](https://learn.microsoft.com/azure/well-architected/security/)
- [Azure AI Foundry Documentation](https://learn.microsoft.com/azure/ai-foundry/)
- [Responsible AI in Azure](https://learn.microsoft.com/azure/well-architected/ai/responsible-ai)
- [AI Agent Business Strategy](https://learn.microsoft.com/azure/cloud-adoption-framework/ai-agents/business-strategy-plan)

### Zero Trust Pillars
- [Identity](https://learn.microsoft.com/security/zero-trust/deploy/identity)
- [Endpoints](https://learn.microsoft.com/security/zero-trust/deploy/endpoints)
- [Data](https://learn.microsoft.com/security/zero-trust/deploy/data)
- [Applications](https://learn.microsoft.com/security/zero-trust/deploy/applications)
- [Infrastructure](https://learn.microsoft.com/security/zero-trust/deploy/infrastructure)
- [Networks](https://learn.microsoft.com/security/zero-trust/deploy/networks)

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) for details.

---

**Presenter**: [Your Name]  
**Contact**: [your.email@domain.com]  
**Session Date**: [Event Date]
