# CST8919 Lab3: Enforcing Organizational Policies in the Cloud

## Lab Overview
In this lab, I implemented governance controls using Azure Policy to location restrict deployments, enforce tagging, and block public IP creation.

## Part 1: Policies Implemented
1. **Only-CanadaCentral**: Denies resources not deployed in Canada Central.
<img width="1909" height="902" alt="image" src="https://github.com/user-attachments/assets/2b19d646-f03e-447d-8129-24fe2e6b67ce" />
2. **Require-ProjectName-Tag**: Enforces a `ProjectName` tag on all resources.
<img width="1906" height="905" alt="image" src="https://github.com/user-attachments/assets/811e3bf9-1694-45e7-b1bf-23559e2c2c2b" />
3. **Deny-Public-IP**: Blocks the creation of public IP addresses.
<img width="1906" height="903" alt="image" src="https://github.com/user-attachments/assets/bf25c4ff-5faf-45f7-9309-72d25fcfbf0e" />


## Part 2 & 3: Policy Initiative
- Name: **MapleTech Secure Foundation**
- Includes all three policies
- Assigned to a resource group with `Enforce` mode
<img width="1905" height="905" alt="image" src="https://github.com/user-attachments/assets/8511adde-7eb8-47ec-b1f5-f410346439d3" />
<img width="1905" height="905" alt="image" src="https://github.com/user-attachments/assets/c80deb53-95ec-410e-947a-5cd4e310dbcf" />


## Part 4: Test Cases & Results
| Test | Result |
|------|--------|
| VM in East US | ❌ Denied |
| Storage Account w/o tag | ❌ Denied |
| Create Public IP | ❌ Denied |
| VM in Canada Central with tag | ✅ Allowed |

Test 1: VM in East US
<img width="1907" height="908" alt="image" src="https://github.com/user-attachments/assets/b8641119-9bd9-4218-b389-6add5d0c60ea" />

Test 2: Storage account without tag
<img width="1907" height="910" alt="image" src="https://github.com/user-attachments/assets/efb66b24-57c2-4f26-ae9c-d32310e66603" />
<img width="1906" height="907" alt="image" src="https://github.com/user-attachments/assets/3190b51b-b920-4139-b979-15cb9d2d2c58" />

Test 3: Create public IP
<img width="1904" height="913" alt="image" src="https://github.com/user-attachments/assets/6d2c1f89-488d-429a-8524-35d921d09883" />

Test 4 VM in Canada with tag
<img width="1909" height="897" alt="image" src="https://github.com/user-attachments/assets/4de31665-a8ee-448c-8eb4-9f8abc2bba44" />
<img width="1904" height="912" alt="image" src="https://github.com/user-attachments/assets/fff93f44-27d4-4b0a-b38b-63af3b43d06b" />
<img width="1906" height="905" alt="image" src="https://github.com/user-attachments/assets/23983836-9c1c-4ace-84b9-9d63f3b05a85" />


## YouTUbe Demo Video
https://youtu.be/V2unVu_-IDI

## Lessons Learned
- Azure Policy is powerful for enforcing compliance without manual oversight.
- Initiative groups simplify applying multiple guardrails consistently.
- Be mindful of scope when assigning policies to avoid broad disruption.

## Challenges
- Testing required waiting for policy propagation (~5–15 min).
- Some resources required more detailed parameter configuration for tags.
