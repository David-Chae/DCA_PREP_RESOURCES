## 24. Tracy has a Docker Trusted Registry (DTR), and her development team mistakenly overwrote images in a repository by pushing a different image with an existing tag. How can she prevent this from happening?
```sh
A. Tracy can back up the registry.
B. Tracy can make the repository private
C. Tracy can remove the team's access to the registry.
D. Tracy can mark the repository as immutable
```

Let's analyze each option for preventing accidental overwrites of images in a Docker Trusted Registry (DTR):

### **A. Tracy can back up the registry.**  
**False** – While backing up the registry is a good practice for disaster recovery, it does not prevent images from being accidentally overwritten in the first place. A backup would allow recovery after the fact but does not provide proactive protection.

### **B. Tracy can make the repository private.**  
**False** – Making a repository private only restricts who can access it, but it does not prevent users who already have push access from overwriting images. The issue here is accidental overwrites, not unauthorized access.

### **C. Tracy can remove the team's access to the registry.**  
**False** – Completely removing access is not a practical solution because the development team still needs to push images. The goal is to prevent overwrites, not block all contributions.

### **D. Tracy can mark the repository as immutable.**  
**True** – Marking a repository as **immutable** prevents tags from being overwritten. Once an image is pushed with a tag, no one can overwrite that tag with a new image, effectively preventing the accidental overwriting issue described in the question.

### **Conclusion:**  
- **Correct Answer:** **D. Tracy can mark the repository as immutable.**  
- **Other options are incorrect** because they either do not address the problem directly or are impractical.

