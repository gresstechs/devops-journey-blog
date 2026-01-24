# Week 2 Reflection: From Tutorial Hell to Deployment Confidence

![DevOps Journey](https://images.unsplash.com/photo-1667372393119-3d4c48d07fc9?w=800)

> *"The confidence I was waiting for? It came — not before the action, but after."*

---

## 📌 What I Set Out to Do

In Week 1, I made a commitment: deploy **2 projects every month** and dedicate **30 hours weekly** to learning. Week 2 was the first real test of that commitment. The assignments shifted from self-reflection to hands-on technical work — and I was nervous.

Could I actually do this? Or would I freeze like I always did?

---

## 🚀 What I Actually Did

I deployed **3 projects** in one week:

| # | Project | Platform | Technology |
|---|---------|----------|------------|
| 1 | React App | AWS EC2 | Ubuntu, Node.js, Nginx, Git |
| 2 | GameStore Website | AWS Lightsail | Vite, React, Nginx |
| 3 | Professional Portfolio | AWS EC2 | Static HTML/CSS, Nginx |

I also completed a full **Production Maintenance Drill** — checking networking, service health, logs, system resources, configuration integrity, and even simulating a real incident where I broke Nginx and recovered it.

---

## 🔥 Challenges I Faced (And How I Solved Them)

### Challenge 1: "Site can't be reached" on Lightsail

I panicked. Everything looked correct, but the browser wouldn't load my site.

**Solution:** It was browser cache. Testing in incognito mode revealed the site was actually working. 

**Lesson:** Always test in incognito when debugging deployments.

---

### Challenge 2: Server ran out of RAM (99% used)

Lightsail's free tier has only 416MB RAM. When I ran `npm run build`, the server froze completely.

**Solution:** I added a 1GB swap file to use disk space as virtual memory:

```bash
sudo fallocate -l 1G /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

The build completed successfully after that.

**Lesson:** Small servers need swap space for memory-intensive tasks.

---

### Challenge 3: Build folder wasn't where I expected

I kept looking for a `build` folder but it didn't exist. I almost gave up.

**Solution:** I realized this was a Vite project, not Create React App. Vite outputs to `dist`, not `build`. 

**Lesson:** Read the project structure before assuming. `ls` is your friend.

---

### Challenge 4: Nginx config broke the entire server

During the incident simulation, I introduced a syntax error. Nginx refused to start. The website went down completely.

**Solution:** I read the error message carefully — it told me the exact file and line number. Fixed the syntax, ran `nginx -t` to validate, restarted the service, and the site came back online.

**Lesson:** Always run `nginx -t` before restarting in production.

---

### Challenge 5: `/var/www/html` directory didn't exist

When deploying the portfolio site, the copy command failed because the directory wasn't there.

**Solution:** Simple fix: 

```bash
sudo mkdir -p /var/www/html
```

**Lesson:** Not every server comes pre-configured the same way.

---

## 📚 Key Learnings

### Technical Skills Gained

- ✅ Launching and configuring EC2 and Lightsail instances
- ✅ Installing Node.js, npm, Nginx, and Git on Ubuntu
- ✅ Building and deploying React (CRA and Vite) applications
- ✅ Configuring Nginx to serve static files and SPAs
- ✅ Reading and analyzing logs (access.log, error.log, journalctl)
- ✅ Checking system resources (CPU, memory, disk)
- ✅ Creating swap space to handle memory limitations
- ✅ Troubleshooting and recovering from service failures

### Mindset Shifts

1. **Errors are teachers, not blockers.** Every error message contains the solution if you read it carefully.

2. **Tutorials teach concepts; deployments teach skills.** I learned more from troubleshooting real problems in one week than from months of videos.

3. **Simple solutions often work best.** The portfolio site didn't need React or a build process — just HTML, CSS, and two commands.

4. **Recovery is as important as building.** Knowing how to fix a broken server is a job-ready skill.

5. **Repetition builds speed.** My first deployment took hours. My third took minutes. Same process, more confidence.

---

## 🔗 Connection to My Week 1 Goals

In Week 1, I wrote:

> *"I've been learning DevOps for a couple of years now — watching YouTube tutorials from various instructors and picking up tools like Docker, Kubernetes, Jenkins, Terraform, and AWS. On paper, I 'know' a lot. But here's the truth: I still don't feel confident enough to apply for jobs."*

**Week 2 changed that.**

I didn't just watch someone deploy an app. I deployed three myself. I didn't just read about Nginx troubleshooting. I broke it and fixed it with my own hands.

The confidence I was waiting for? It came — not before the action, but after.

---

## ⏭️ What I'm Taking Into Week 3

1. **Keep deploying.** The goal is 2 projects per month. I've already exceeded January's target, but momentum matters.

2. **Document everything.** The OPS checklist taught me that real DevOps engineers don't just run commands — they record evidence and write conclusions.

3. **Embrace the struggle.** Every challenge this week made me better. I'll stop avoiding hard problems and start seeking them.

4. **Stay consistent.** My 5-month system plan from Week 1 is working. Early morning deep work sessions are where real progress happens.

---

## 💭 Final Thought

Week 1 asked me who I wanted to become.

Week 2 showed me I'm already becoming that person.

**One deployment at a time.**

---

## 🔗 My Live Deployments

| Project | URL |
|---------|-----|
| React App | [http://ec2-18-130-51-118.eu-west-2.compute.amazonaws.com](http://ec2-18-130-51-118.eu-west-2.compute.amazonaws.com) |
| GameStore | [http://13.40.94.10](http://13.40.94.10) |
| Portfolio | [http://18.171.187.134](http://18.171.187.134) |

---

## 📬 Connect With Me

- [LinkedIn](https://linkedin.com/in/YOUR-LINKEDIN)
- [GitHub](https://github.com/YOUR-GITHUB)
- [Twitter](https://twitter.com/YOUR-TWITTER)

---

**Author:** Chidera Progress Nwaokwa  
**Program:** DMI Cohort-2 | Group 2  
**Date:** January 2026

---

*P.S. This post is part of the DevOps Micro Internship (DMI) Cohort-2 by [Pravin Mishra](https://www.linkedin.com/in/pravin-mishra-aws-trainer/). You can start your DevOps journey by joining this WhatsApp community.*

---

**Tags:** `#DevOps` `#AWS` `#LearningInPublic` `#CloudComputing` `#Nginx` `#TechJourney` `#DMI` `#BuildInPublic`
