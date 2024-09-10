#priviledgeEscalation #windows 

We can use a few other methods to access the system as another user when certain requirements are met. We can use WinRM or RDP to access the system if the user is a member of the corresponding groups. Alternatively, if the target user has the _Log on as a batch job_[6](https://portal.offsec.com/courses/pen-200-2023/books-and-videos/modal/modules/windows-privilege-escalation/enumerating-windows/hidden-in-plain-view#fn6) access right, we can schedule a task to execute a program of our choice as this user. Furthermore, if the target user has an active session, we can use _PsExec_ from Sysinternals

[[1. PrivEsc Recon Enum|1. PrivEsc Recon Enum]]
[[Escalation Methods]]
[[Service DLL Hijacking]]
[[Service Binary Hijacking]]
[[Unquoted Service Paths]]
[[2. Scheduled Tasks]]


