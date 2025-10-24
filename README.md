# CS-360

App code design artifact

This repository contains my Event Tracking Android app and the completed app code design ZIP from Project Three, including the finalized UI design that I initially drafted in Project Two and refined during development.

Reflection

My goal for this app was to give users a fast, reliable way to capture and review events in their day: title, date and time, location or context notes, and an optional reminder. The primary user needs I targeted were quick entry with guardrails to prevent bad data, effortless browsing with search and filters, and a clean UI that is readable on small screens and in dark mode.

To support those needs I built a simple flow: a home screen with a scrollable list of events, an add or edit screen with validation, a detail view, and lightweight search and filter controls. The list uses a RecyclerView so large lists stay smooth. Date and time pickers reduce typing and mistakes, and Material components keep spacing, contrast, and touch targets consistent. The designs worked because I kept the number of decisions per screen low and made the primary action obvious.

For coding I followed a small MVVM structure with a Room database, a DAO for queries, a repository to isolate data access, and ViewModels that expose LiveData to the UI. This separation made testing simpler and eliminated a lot of lifecycle bugs. Kotlin coroutines keep database work off the main thread. These same techniques can be reused in future apps to keep features modular and testable.

I tested functionality with a mix of unit tests and hands-on device testing. DAO unit tests verified inserts, updates, deletes, and common queries. On device, I checked orientation changes, empty states, large text accessibility, and edge cases like duplicate titles or very long notes. This matters because small data errors compound quickly in personal tracking apps, and catching them early prevents broken user trust.

Looking at the full design-to-finalization process, the biggest challenge was coordinating lifecycle, database updates, and UI refreshes without freezing the app. Moving the data layer behind a repository and using LiveData plus coroutines solved that. I also iterated on the list screen several times before it felt “frictionless.” That iteration was worth it: a single extra tap removed per action adds up over daily use.

The component I’m most proud of is the Room plus search pipeline. It supports instant filtering while the list remains responsive, and the code is small, readable, and easy to extend. That piece demonstrates my growth in Android patterns, data modeling, and user-centered thinking—keeping performance and clarity front and center while meeting real user needs.
