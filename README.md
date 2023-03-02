# The Tutors Open Source Project

A Final Report by Jordan Harrison

Higher Diploma in Computer Science

Department of Computing & Mathematics, SETU Waterford

20095937@mail.wit.ie / contact@jordanharrison.ie

## Table of Contents

- [The Tutors Open Source Project](#the-tutors-open-source-project)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
    - [Background](#background)
    - [Objectives](#objectives)
    - [Motivation](#motivation)
  - [Educational Technology (EdTech)](#educational-technology-edtech)
  - [State of the art](#state-of-the-art)
    - [NodeJS \& TypeScript](#nodejs--typescript)
    - [Frontend Frameworks](#frontend-frameworks)
    - [CSS Frameworks \& UI Libraries](#css-frameworks--ui-libraries)
    - [Build Systems](#build-systems)
    - [Monorepos](#monorepos)
  - [Architecture](#architecture)
    - [Under the hood](#under-the-hood)
    - [Tutors Course Reader](#tutors-course-reader)
    - [Tutors Reader Lib](#tutors-reader-lib)
    - [Tutors UI](#tutors-ui)
  - [Implementation](#implementation)
    - [Pre-Project (Early 2021 - August 2022)](#pre-project-early-2021---august-2022)
      - [Initial Technologies \& User Experience](#initial-technologies--user-experience)
      - [Initial Setup \& Research](#initial-setup--research)
      - [Implementing DaisyUI](#implementing-daisyui)
      - [Tutors Tech Team](#tutors-tech-team)
        - [Red Hat Onboarding](#red-hat-onboarding)
        - [Working with the Tutors Tech Team](#working-with-the-tutors-tech-team)
        - [A new Tutors domain \& branding](#a-new-tutors-domain--branding)
        - [Meeting Red Hat](#meeting-red-hat)
    - [Project Implementation (August 2022 - March 2023)](#project-implementation-august-2022---march-2023)
      - [The Tutors Monorepo](#the-tutors-monorepo)
        - [Turborepo](#turborepo)
        - [Creating the Tutors Monorepo](#creating-the-tutors-monorepo)
      - [The Tutors Design System](#the-tutors-design-system)
      - [Netlify Open Source License](#netlify-open-source-license)
      - [Developer Events](#developer-events)
        - [Hacktoberfest 2022](#hacktoberfest-2022)
        - [GDG Glasgow 2022](#gdg-glasgow-2022)
      - [The Next Generation of Tutors](#the-next-generation-of-tutors)
        - [SvelteKit \& Skeleton](#sveltekit--skeleton)
        - [SvelteKit](#sveltekit)
        - [Skeleton, Storybook \& tutors-ui components](#skeleton-storybook--tutors-ui-components)
        - [An updated monorepo structure](#an-updated-monorepo-structure)
        - [Preparing for release](#preparing-for-release)
  - [Conclusion + Further work](#conclusion--further-work)

## Introduction

### Background

The Tutors Open Source Project is a collection of components & services supporting the creation of transformative learning experiences using open web standards. The project supports 3 complementary perspectives - the Learner, Educator & Developer experiences. It was originally developed by Eamonn de Leastar, beginning around 10 years ago as a python application with similar principles as it has today - ingesting markdown content to generate either a static site or a zip file which could be uploaded as a lab to Moodle. It has evolved over the past decade, keeping to the same principles, but has been adapted to use modern technologies.

In the summer of 2021, on the 3rd of June, I approached Eamonn De Leastar, a SETU lecturer and the developer of Tutors, with the intention of setting up the Tutors software on my local machine. My goal was to familiarize myself with the codebase and improve the user experience for learners. From that point on, I actively participated in the project, working on it consistently. Although it is unorthodox, I organically onboarded to the Tutors project early on in the course, and as a result grew as a developer because of Tutors and built something that I am proud of.

### Objectives

My objectives for this project were as follows:

1. Create a more engaging learner experience, with a fresh, modern interface & improved user experience.
2. Improve the developer experience by creating a monorepo and tidying up the codebase.
3. Open up the project to contributions from the open source developer community.
4. Bring exposure to the Tutors Open Source Project by presenting it to a wider audience.

### Motivation

In the first semester of my studies, I became a frequent user of Tutors, an educational software. As I used the software on a daily basis, I noticed that the user experience was lacking. Specifically, I found that the software did not have a self-explanatory interface and required users to seek explanations in order to navigate it. This realization motivated me to want to get involved with the project and work on the codebase in order to modernize the frontend design, with the goal of making Tutors more user-friendly for myself and others during the course of my studies. As I began to delve deeper into the project, I developed an acute appreciation for Tutors and became actively engaged in its development. This experience ultimately led me to choose Tutors as the subject of my final project.

## Educational Technology (EdTech)

In recent years, the rapid advancement of technology has transformed the way we teach and learn. Educational technology, or edtech, has become an increasingly popular tool in classrooms worldwide, as it provides a more interactive and engaging learning experience for students. One of the most widely used edtech tools is the Virtual Learning Environment (VLE), which allows educators to deliver educational content online. Moodle, an open-source VLE, has gained popularity due to its customizable and user-friendly nature, making it an exemplar of the power and potential of edtech.

It's worth noting that there are other online learning platforms that differ from it in some significant ways. Massive Open Online Courses (MOOCs), such as edX and Coursera, are designed to offer free or low-cost online courses to a vast audience of learners worldwide. On the other hand, online environments like Udemy are more geared towards commercial offerings, with instructors creating and selling courses to students. While these platforms can be a great way to learn new skills or gain knowledge, they lack the level of customization and personalization offered by a VLE.

VLEs allows educators to tailor the learning experience to their students' needs and provides a collaborative learning environment that promotes student engagement and interactivity. They offer more opportunities for collaboration and communication between students and instructors - through features like forums, messaging, and video conferencing, students can interact with their peers and teachers, fostering a sense of community and creating a more social learning environment. They also allow students to access educational content at their own pace, allowing them to learn at their own pace and in their own time.

While MOOCs and tutorial sites may offer courses on specific topics, VLEs can provide a complete education experience with integrated courses, assessments, and support systems. Overall, VLEs are a great way to provide a more engaging and interactive learning experience for students, and they are becoming increasingly popular in classrooms worldwide.

## State of the art

The latest web technologies has transformed the way we build web applications, providing developers with powerful tools to create fast and reliable web applications. In this section we are going to be looking into the technologies that has been implemented in Tutors and how they compare to older technologies.

### NodeJS & TypeScript

NodeJS is an open-source, cross-platform, JavaScript runtime environment that allows developers to run JavaScript code outside of a web browser. NodeJS is built on the V8 JavaScript engine, the same engine used by Google Chrome, and provides developers with access to a rich set of libraries and modules that allow for the creation of server-side applications. It has a non-blocking I/O model, which means that it can handle multiple requests simultaneously, making it an ideal choice for building scalable and high-performance applications.

TypeScript is a superset of JavaScript that adds optional static typing and other advanced features to the language. TypeScript is fully compatible with NodeJS and provides several benefits over traditional JavaScript. It has excellent interoperability with existing JavaScript code, allowing developers to gradually adopt TypeScript without rewriting their entire codebase. TypeScript enables developers to catch errors early in the development process, reducing the likelihood of bugs and errors in production. This is because TypeScript checks types at compile time, providing early feedback on any type mismatches. It also provides developers with better tooling and IDE support, making it easier to navigate and maintain larger codebases.

NodeJS is a powerful JavaScript runtime environment that allows developers to build high-performance applications. TypeScript provides advanced features like optional static typing and better tooling, which improve the development experience and reduces the likelihood of bugs and errors in production. By using NodeJS with TypeScript, developers can take advantage of the benefits of both technologies, creating scalable, high-performance, and maintainable applications.

### Frontend Frameworks

Frontend frameworks are a collection of libraries and tools that allow developers to build web applications. They allow developers to build web applications quickly and efficiently, allowing them to focus on the core functionality of their application. Some of the most popular frontend frameworks include React, Vue, Svelte and Angular. Each framework has its own set of features and benefits, but they all share a common goal - to make it easier for developers to build web applications.

SvelteKit, a relatively new framework based on Svelte, has gained popularity due to its lightweight, fast, and flexible nature, making it an excellent choice for building modern web applications. It is built on top of the Svelte compiler, which allows developers to build web applications using a component-based approach. SvelteKit also provides a number of features that make it easier to build web applications, including a router, a store, and a server-side rendering engine. Unlike React, Vue and other frameworks, SvelteKit compiles components during build time, which reduces the size of the final bundle and improves application performance, along with eliminating the need for virtual DOM, resulting in a faster and more efficient runtime. Additionally, SvelteKit is easy to learn and use, providing developers with a simple and intuitive syntax that requires less boilerplate code.

### CSS Frameworks & UI Libraries

A CSS framework is a pre-designed set of CSS styles and rules that help developers build responsive and visually appealing user interfaces quickly. These frameworks provide a collection of CSS classes that define common UI elements like buttons, forms, and layouts. By using a CSS framework, developers can save time and effort by not having to create styles from scratch. Some of the most popular CSS frameworks include Bootstrap, Tailwind CSS, and Bulma.

Tailwind CSS is a framework that provides developers with a utility-first approach to styling web applications. This means that instead of using predefined CSS classes, developers can use a set of utility classes to create responsive and customizable user interfaces quickly. Tailwind CSS comes with a learning curve compared to typical CSS frameworks, but it provides massive set of pre-defined classes that cover everything from layout and typography to color and spacing. This approach not only speeds up the development process but also allows developers to create consistent and visually appealing user interfaces with ease. Additionally, Tailwind CSS is highly customizable, allowing developers to create their own utility classes and adjust the default settings to fit their specific needs.

Skeleton is a UI library that provides developers with a collection of pre-designed components that can be used to build web applications. It is built specifically for SvelteKit projects and is built on top of Tailwind CSS, which means that it provides developers with a consistent yet customizable user interface. Skeleton is a great choice for developers who want to build web applications quickly and efficiently, as it provides a collection of pre-designed and functional components.

### Build Systems

Build systems play a vital role in modern web development, allowing developers to compile, bundle, and optimize their code for production. One popular build system, Webpack, has been the go-to tool for many years and has been pre-bundled with most modern frontend frameworks. However, Vite has emerged as has objectively became a better option due to its faster build times and improved development experience. Vite takes advantage of modern browser features like ES modules and lazy-loading to improve build times significantly. This means that instead of bundling all code upfront, Vite can compile and load code on the fly as it's needed, reducing build times and improving development workflow. Additionally, Vite provides a better development experience with features like hot module replacement, which allows developers to see changes to their code in real-time without reloading the page.

### Monorepos

Monorepos are a more recent approach to managing codebases that contain multiple projects or applications. Instead of having separate repositories for each project (polyrepos), a monorepo houses all the projects in one, structured repository. This approach offers several advantages over polyrepos, including better code sharing, improved code quality and streamlined development workflows. With a monorepo, developers can share code between projects more easily, reducing the need for duplicate code, improving code reuse and promoting better code quality, as developers can maintain a single codebase with consistent coding standards and practices. A monorepo simplifies the development workflow by allowing developers to manage multiple projects with a single set of tools and processes, and allows for easier management of dependencies, as developers can manage dependencies for all projects in a single place.

## Architecture

//Todo, write about pre-project vs post-project architecture.

### Under the hood

The Tutors project is a monorepo, which contains all the code for the Tutors project. It is built using TurboRepo, which allows us to have a single repository for the Tutors project, which contains all the code for the project, and allows us to manage the dependencies of the project in a single place. It embraces the JAMStack architecture, which is a modern architecture for building web applications.

All Tutors applications are built on top of [NodeJS](https://nodejs.org/en/), a cross-platform JavaScript runtime environment, and are written in [TypeScript](https://www.typescriptlang.org/), a typed superset of JavaScript that compiles to plain JavaScript. The advantage of using TypeScript is that it allows us to write code in a typed manner, which allows us to catch errors at compile time, rather than at runtime. This is especially useful when working with a large codebase, as it allows us to catch errors early on, and to ensure that the code is well structured and easy to read.

Tutors' web applications are built with [SvelteKit](https://kit.svelte.dev/), a framework which is built on top of Svelte. The user interfaces are built using [Skeleton](https://skeleton.dev), a UI library built specifically for SvelteKit which is built on top of [TailwindCSS](https://tailwindcss.com/). Firebase Realtime Database is for data storage, Auth0 for authentication, GitHub for code storage, and Netlify for hosting.

### Tutors Course Reader

The Tutors Course Reader is the main front end application of the Tutors project. It is a web application which consumes the JSON output of the tutors-json package (usually hosted on Netlify) and renders a course for student consumption. It is built using SvelteKit, and relies on 2 components, `tutors-ui` and `tutors-reader-lib`. `tutors-ui` is the design system which contains all the UI components responsible for rendering the core elements of the reader. `tutors-reader-lib` is a Typescript library which contains all the logic for the Tutors Course Reader, and is responsible for loading the course from the remote server, long with starting up and driving the metrics & presence models which are used to track student progress & show online status.

### Tutors Reader Lib

The `tutors-reader-lib` package is where a lot of the 'heavy lifting' is done in downloading the course from the remote service & building up, within the browser, an in-memory model of the course. There is course, lab & topic models, services for analytics, authentication, course, metrics & presence, a stores for the course & some types for authentication, icons, lo (learning objects), metrics & stores.

### Tutors UI

The `tutors-ui` package is the design system for the Tutors project. It is built on top of Skeleton, a UI library built specifically for SvelteKit. Skeleton is based on TailwindCSS, and provides a lot of components, utilities & stores which we use to build out the Tutors Course Reader. It also provides a lot of flexibility in terms of how the application is structured, allowing for a lot of customisation.

## Implementation

### Pre-Project (Early 2021 - August 2022)

#### Initial Technologies & User Experience

The initial frontend of Tutors when I started the course was built with Aurelia and used UI Kit for the design (see fig. 1). By the time I had started working on Tutors it had been upgraded to be built with Svelte and TailwindCSS (see fig. 2).

![Tutors Aurelia](images/tutors-aurelia.png)

Figure 1 - Tutors Aurelia

![Tutors Svelte](images/tutors-svelte.png)

Figure 2 - Tutors Svelte

#### Initial Setup & Research

As a student early in my course of study, I had limited experience with frontend development. In order to familiarize myself with the codebase of the Tutors project, I dedicated multiple evenings to learning various tools and technologies such as Git, running code on a local machine, and navigating the codebase to understand its various components. I then conducted research on the tech stack being used, which included Svelte and TailwindCSS, and explored various UI libraries that could potentially improve the user experience when used in conjunction with these technologies. It was during this research that I discovered [Daisy UI](https://daisyui.com), an open-source UI component library built on top of TailwindCSS that provides a simplified approach to building User Interfaces through the use of pre-defined component classes.

#### Implementing DaisyUI

After confirming that DaisyUI's component library would provide comprehensive coverage for all components needed in Tutors, I proceeded to implement the library in the project. The initial wireframe was created using a combination of TailwindCSS and DaisyUI via Stackblitz, an online code editor. The code for this stage of the project can be accessed [here](https://stackblitz.com/edit/daisyui-svelte-vite-cfhqdw?file=src/App.svelte).

During the implementation of DaisyUI I experimented with the colour styles, implemented the [theme-switch](https://github.com/saadeghi/theme-change) for dark mode & changing themes and the [iconify](https://icon-sets.iconify.design) package for icons. For a more comprehensive overview of my work on this phase of the project, I wrote a blog post which can be seen [here](https://jord.dev/a-summers-work-redesigning-wits-tutors-open-source-software-using-daisyui). In below figures 3 - 7 I have provided work in progress screenshots of this implementation.

![Tutors wireframe with DaisyUI](images/tutors-daisyui-wireframe.png)

Figure 3 - Tutors early wireframe with DaisyUI

![Tutors mobile responsive wireframe with DaisyUI](images/tutors-daisyui-wireframe-mobile.png)

Figure 4 - Tutors early wireframe - mobile responsiveness

![Early work on progress of implementing DaisyUI in Tutors](images/tutors-daisyui-early-wip.png)

Figure 5 - Early work in progress implementing DaisyUI in Tutors

![Early work on progress of implementing DaisyUI in Tutors](images/tutors-daisyui-early-wip-2.png)

Figure 6 - Mid work in progress implementing DaisyUI in Tutors

![Early work on progress of implementing DaisyUI in Tutors](images/tutors-daisyui-late-wip.png)

Figure 7 - Late work in progress implementing DaisyUI in Tutors

#### Tutors Tech Team

##### Red Hat Onboarding

In August 2021, following the successful build and release of Tutors incorporating DaisyUI, Eamonn De Leastar, the developer of Tutors, approached me with an invitation to join the Tutors technical team. At this point, Red Hat had agreed to provide resources for further development of Tutors, including the appointment of a project manager and two engineers to work on Tutors one day a week, with regular meetings to discuss progress on the project. I was excited to have the opportunity to continue contributing to the user experience of Tutors as part of this team.

##### Working with the Tutors Tech Team

As part of the Tutors technical team, I worked on the following tasks:

- Creation of new 'Tutors' and 'Tutors Dark' theme with accessible colour schemes
- Creation of a dyslexia-friendly theme using the Open Dyslexic font and an easier to read colour scheme
- Implementation of the 'presence' feature and design a dropdown menu for the user's profile & show online status and number of users online
- Minor UI improvements to the Tutors interface such as a new menu bar style, coloured borders on cards, better mobile responsiveness and iconography changes

![Preview of the initial implementation of presence](images/tutors-presence-initial.png)

Figure 8 - Preview of the initial implementation of presence

##### A new Tutors domain & branding

In addition to the work I did on the Tutors codebase, I also worked on the creation of a new domain for Tutors, [tutors.dev](https://tutors.dev). The domain was set up to be used alongside, and later replace, the existing Tutors instance on a netlify subdomain. This was done in order to provide a more user-friendly URL for learners to access Tutors and provide a more accessible sole location for the project, with subdomains for each component of the project.

I also worked on a rebrand of tutors with a new, custom logo I designed in Adobe Illustrator (see fig. 9). The logo was designed to be simple, modern and memorable, and to be used in conjunction with the new domain name.

![Tutors logo](images/tutors-logo.png)

Figure 9 - Tutors logo

##### Meeting Red Hat

In April 2022 I had the opportunity to visit the Red Hat office in Waterford to attend a meeting with the Tutors technical team. During this meeting, we discussed the progress made on the project and the future of Tutors. The meeting was a great opportunity to meet the other members of the team and to discuss the project in person. I presented the UI changes made along with the new tutors logo & domain. I also presented the new themes I had created for Tutors, including the dyslexia-friendly theme. During the meeting, we also got the opportunity to do a [10-for-10](https://openpracticelibrary.com/practice/10-for-10/) brainstorming workshop. This was a great opportunity to discuss the future of Tutors and to get feedback from the team on the project.

![Red Hat Waterford office](images/red-hat-waterford-office.jpg)

Figure 10 - Red Hat Waterford office

### Project Implementation (August 2022 - March 2023)

#### The Tutors Monorepo

My next task was to create a monorepo for the Tutors project. This was done to create a single repository which developers can work in on all parts of the Tutors Open Source Project, instead of requiring them to pull multiple repositories to make changes. This provided a more streamlined development experience for contributors to the project. After a lot of research and consideration, I decided that the monorepo would be made using [Turborepo](https://turbo.build), a tool for managing monorepos.

##### Turborepo

Turborepo is a tool for managing monorepos. It is a command line tool which allows developers to create a monorepo using a single command. The reason I decided to proceed with Turborepo over other monorepo tools such as [Lerna](https://lerna.js.org/) and [Yarn Workspaces](https://classic.yarnpkg.com/en/docs/workspaces/) is that is is built by a well-backed company (Vercel) and is actively maintained. It is very well documented and provides a lot of features out of the box, such as the ability to run scripts across multiple packages in the monorepo, and the ability to run scripts in parallel. It also provides a lot of flexibility in terms of how the monorepo is structured, which allowed be to to create a monorepo which suited the Tutors Project's needs.

##### Creating the Tutors Monorepo

Before starting to create the monorepo, I had to decide on the structure of the monorepo. After considering this with Eamonn, we decided to structure the monorepo in the following way:

The root of the monorepo would contain the following folders:

- `apps` - this would contain all of the command line applications in the monorepo
- `components` - this would contain the reusable components of the monorepo
- `sites` - this would contain the frontend websites of the monorepo

This structure would allow us to create a monorepo which would be easy to navigate and would allow us to easily add new applications and components to the monorepo in the future. We wanted to get the monorepo up and running in a timely manner, to attract developers to the project during the Hacktoberfest 2022 event and to make sure that the monorepo was easy to navigate and understand for the new contributors that would come on board to the project.

This monorepo structure was then added to a new repository on GitHub, [tutors-sdk/tutors](https://github.com/tutors-sdk/tutors), which was named to ensure the project was easily searchable on GitHub. To ensure it was easily identifiable as the main repository for the Tutors project, it was pinned to the top of the tutors-sdk profile.

#### The Tutors Design System

Alongside the monorepo, I decided to put time into building out a design system for the Tutors project. This was done to provide a consistent user experience across all of the Tutors applications and to make it easier for developers to contribute to the project. In order to fill out this package with components, I taken an [atomic design](https://bradfrost.com/blog/post/atomic-web-design/) approach to the design system. This approach involved breaking down the design system into smaller components, which could then be combined to create more complex components. This approach allowed for a more modular design system, which can be easily extended and modified in the future.

Initially, this was built in the `lib` folder of the course reader application, but later was formed into it's own package in the monorepo. This was done to make it easier for developers to access the design system, allowing multiple applications to use it's components, and to make it easier to maintain the design system in the future.

#### Netlify Open Source License

With the new domain and branding in place, and a single repository for the Tutors project, I worked with Eamonn to apply for a [Netlify Open Source](https://www.netlify.com/legal/open-source-policy/) License. This license provided Tutors with a Netlify Open Source license on our account, which provided us with the same level of features as the Netlify pro plan, such as access from the organization github repo, multiple concurrent builds, a larger bandwidth allocation, multiple user access, shared environment variables & continuous deployment. This was a great opportunity to provide Tutors with a more reliable hosting solution and to provide the project with a more professional look.

In order to prepare Tutors for the Netlify Open Source License, I worked on the following tasks:

- Cleanup of the deployed code on the Tutors netlify account to only include the open source projects
- Create a code of conduct for the project
- Ensure the license for the project was included in the repository
- Add the netlify logo to the footer of the Tutors website
- Add the netlify badge to the README of the Tutors repository

#### Developer Events

##### Hacktoberfest 2022

Come the end of September 2022, the Tutors repo was ready for participants to come on board during Hacktoberfest, an event which attracts and encourages developers to work on Open Source projects, with companies giving out free swag for participants. It was an ideal opportunity to get the word out about the Tutors project and to attract new contributors to the project. I worked with Eamonn to create a list of issues for contributors to work on during Hacktoberfest. These issues were a mix of bug fixes, feature requests and documentation improvements.

As you can see [here](https://github.com/tutors-sdk/tutors/pulls?q=is%3Apr+is%3Aclosed+merged%3A2022-10-01..2022-10-31) 41 pull requests were merged during Hacktoberfest 2022, with 16 of these pull requests being raised by 6 new contributors to the project. This was a peak time for contributions to the Tutors repo for the year, as seen in Figure 11 below. This was a great success for the project and was a great opportunity to get the word out about the project and to attract new contributors to the project.

![GitHub Contributions](images/github-contributions.png)

Figure 11 - GitHub Contributions around the time of Hacktoberfest 2022

##### GDG Glasgow 2022

While attending NodeConf EU 2022, I met Patty - one of the organisers of DevFest at Google Developer Group Glasgow. While helping her with her workshop for the conference I got talking about my work on Tutors, and I was invited to speak at GDG Glasgow in November 2022. I was very excited to speak at GDG Glasgow about my experience working on the Tutors project and talk about the architecture of the project, which is outlined further in this report.

In preparation for this talk, I sat down with Eamonn and we discussed the format of the talk and how it would be delivered. We decided that the talk would be a 45 minute deep dive, with 10-15 minutes for questions at the end. We also decided that the talk would be delivered remotely, as I was unable to attend in person. The talk was delivered via livestream to the GDG Glasgow YouTube channel. The recording of the livestream from this talk can be found [here](https://www.youtube.com/watch?v=9j25w4Zrucg).

#### The Next Generation of Tutors

##### SvelteKit & Skeleton

After the success we had during Hacktoberfest 2022, and with the looming new cohort of students coming in January to the HDip course, we decided to move ahead with building the next generation of Tutors. This was a complete rewrite of the Tutors project, using the latest technologies and best practices. The new version of Tutors was to be built using [SvelteKit](https://kit.svelte.dev/), a framework for building web applications using [Svelte](https://svelte.dev/), which is what the previous version of Tutors was built upon. This worked out very timely, as SvelteKit version 1.0 was released when we were starting to work on the new version of Tutors. This meant that we knew we were using a stable, production-ready and well supported framework for the new version of Tutors.

##### SvelteKit

Due to my experience with Svelte, I was very excited to work on the new version of Tutors using SvelteKit. I had been following the development of SvelteKit for a while and was very excited to see it released. I had also been following the development of [Skeleton](https://skeleton.dev), a SvelteKit focused UI library. It was clear that SvelteKit was going to be a great fit for the new version of Tutors, being built on top of Svelte, and providing a lot of important new features, such as server-side rendering and a built in file-based routing system. It also provides a lot of flexibility in terms of how the application was structured, which allowed us to create a structure which suited the Tutors Project's needs.

Eamonn taken the liberty of doing the migration of the current designed Tutors Course Reader to SvelteKit. This was a great opportunity for me to get familiar with SvelteKit and to learn how to use it. I also got the opportunity to work on the new Tutors Course Reader design, which was to be done in Skeleton, and migrate the components of the course reader into the tutors-ui library.

##### Skeleton, Storybook & tutors-ui components

Once the Sveltekit version of Tutors was built, I took to work on the new Tutors Course Reader design and, in turn, create the `tutors-ui` library. This was done in Skeleton, a UI library built specifically for SvelteKit. Skeleton is a UI library which is built on top of TailwindCSS, and provides a lot of components which can be used to build out a SvelteKit application. It also provides a lot of flexibility in terms of how the application is structured, allowing for a lot of customisation. It was much less opinionated than other UI libraries, such as [DaisyUI](https://daisyui.com/), which was a big plus for me as we needed something we could tailor to our needs more.

In order to display the components of the design system, I created a [Storybook instance](https://ui.tutors.dev) for the `tutors-ui` library. I initially looked into alternatives to Storybook, and came across Vitebook - but this ended up being depracated and stopped being maintained after I started working with it, so I settled on Storybook as it is a leader in this space it made sense to go with a well established solution.

##### An updated monorepo structure

In order to facilitate the new version of Tutors, we decided to update the structure of the monorepo. The following was the updated folder structure that we decided on:

- `apps` - this contains all the front end applications in the monorepo
  - `course` - the course reader application built in SvelteKit
  - `home` - the home page of the Tutors project
  - `time` - the tutors time application built in SvelteKit
- `cli` - this contains all the command line applications in the monorepo
  - `tutors-gen` - a new generation tool for emitting json output of courses
  - `tutors-html` - the old html emitter for courses to output a static html website
  - `tutors-json` - the old json emitter for courses to output a json file
- `packages` - this contains all the reusable components of the monorepo
  - `tutors-lib` - the core library for the Tutors project
  - `tutors-reader-lib` - the core library for the Tutors Course Reader
  - `tutors-ui` - the design system for the Tutors project

##### Preparing for release

Once we felt that the new version ofthe tutors course reader was almost ready for release, we decided to do a soft launch. This was done by creating a new branch in the monorepo,along with a new subdomain, which was `alpha.tutors.dev`. This allowed us to test the new version of the Tutors course reader in a production environment, and for lecturers to get early access to the new version to ensure their courses would work seamlessly after the upgrade. A week later, another branch was created as a beta release, which was then deployed to the `beta.tutors.dev` subdomain. This allowed us to get more feedback from a wider audience on the new version of Tutors, being shared to the students on the HDip in Computer Science 2021 and 2022 cohorts, and to iron out any bugs that were found.

Once we felt that the new version of the Tutors course reader was ready for release, we merged the beta branch into the main branch. This was a very exciting moment for the project, as we had put a lot of work into this release, which came with many exciting new features and upgrades, so it was great to see it finally released.

## Conclusion + Further work
