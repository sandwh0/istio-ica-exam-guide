# Istio Certified Associate Training

Practical study material for the Istio Certified Associate exam, built around concise revision notes and exam-style labs.

The goal of this repo is to prepare you for the exam, not to make you an Istio expert.

## What is Istio?
Istio is an open-source service mesh for Kubernetes that helps manage service-to-service traffic, security, and observability.

If you are new to service meshes, start here: [`0-istio-overview/README.md`](0-istio-overview/README.md).

## Structure
There is a directory for each exam topic:

- `0-istio-overview`
- `1-installation-upgrades`
- `2-traffic-management`
- `3-securing-workloads`
- `4-troubleshooting`

Inside each topic directory, you will find:

- A high-level overview to understanding core concepts.
- Labs to practice the topic.
- A `setup.yaml` to prepare your environment for each lab.
- An `answer.yaml` to check your solution.
- Use the cleardown commands to clear resources.

## How to use this repo
- Read the topic overview first.
- Apply the relevant `setup.yaml`.
- Complete the lab before checking the answer.
- Verify your result, then run `cleandown.yaml`.

## Lab Environment Requirements
- You need access to a Kubernetes environment where you can install and modify Istio resources.
- For quick setup, using the Killercoda Istio Sandbox (or a similar hosted lab environment) is recommended.
- You can also run the labs in your local environment.
- It is assumed you are already familiar with Kubernetes.

## Exam Structure
- Prerequisites: there are no prerequisites for this exam.
- The exam is 2 hours long and follows a format similar to the Kubernetes exams.
- The exam consists of 15-20 performance-based tasks.
- Pass mark: 68%.

## Exam Syllabus
- Installation, Upgrade & Configuration (20%)
- Traffic Management (35%)
- Securing Workloads (25%)
- Troubleshooting (20%)

## Recommended Study Resources
- I highly recommend [KodeKloud's ICA course.](https://learn.kodekloud.com/courses/istio-certified-associate)

> ## Please feel free to open a PR if you spot any mistakes, typos, or gaps in the lab content.
