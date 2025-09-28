Neurosurgical SHO Rota Generator

This web application automates the weekly team rota for neurosurgical SHO (senior house officer) rotas. It reads your existing Excel rota, applies a series of staffing rules and preferences, and produces a complete week‑day schedule with clerking duties, daily team allocations, individual doctor timetables, and message text ready for distribution. The page is entirely client‑side—no server or external dependencies beyond a web browser.

Features

Excel import – Upload your weekly rota (an .xlsx file) with a sheet named SHO Rota. The script forwards the team column, detects leave/on‑call/night shifts and determines which doctors are available each day.

Weekday focus – Saturday and Sunday columns are automatically excluded. Only Monday through Friday are scheduled.

Daily workload and extra doctors – For each day, enter the number of admissions requiring clerking and specify how many extra doctors you need for Teams A, B, C and D. The algorithm fills the core roles (Pit/Epi, Functional, PG/WM, AT/LW, PC/MM, Team C1, Team C2, Team D) and assigns extras in order of priority.

Per‑day absences – A dynamic table lists every doctor (except locums and PP). Check the boxes to mark them as absent or ill on specific days. These doctors are excluded from team and theatre assignments for those days.

Fixed assignments – Certain doctors can have fixed team assignments (e.g. always covering a particular ward category) that are respected whenever they are on the ward. These clinicians also participate in the theatre rotation whenever a suitable replacement is available. The mapping of names to categories can be edited in the HTML if your roster changes.

Fair theatre rotation – After core teams are filled, any surplus doctors are sent to theatre. The algorithm ensures no one goes to theatre twice until every other available colleague has had a turn.

Clerking assignments – The tool calculates the minimum number of clerking doctors needed based on admissions (2–3 patients per doctor). It prioritises early starters (07:00), gives everyone a single clerking shift before assigning a second, avoids consecutive days of clerking, skips doctors who are on‑call or on the day after an on‑call, and caps clerking shifts at three per week. Two specific doctors can be excluded from clerking duties altogether (configurable in the script).

Night shifts – Night‑shift doctors are listed separately and excluded from daytime counts.

Individual schedules – A per‑doctor timetable summarises each doctor’s assignments (Team A/B/C/D, Pit/Epi, Functional, PG/WM, AT/LW, PC/MM, Team C, Theatres, Night) for every weekday.

Daily messages – Auto‑generated messages follow your requested format, listing team allocations, bleeps, clerking duty roster, on‑call and night assignments, plus theatre staff.

Printing – Once the rota is generated, you can print or save PDFs of the Weekly Team Allocation and Individual Schedules via the on‑page buttons. Each opens a print‑friendly view with minimal styling ready for your browser’s “Save as PDF” option.

Modern design – The interface uses a clean, card‑style layout with subtle colours, rounded tables and buttons, and responsive spacing. The absences panel sits alongside the daily workload inputs for quick updates.

Usage

Open the file – Double‑click index (13).html (or open it through your browser) to load the application. A modern browser such as Chrome, Edge or Firefox is recommended.

Upload the rota – Click Choose File and select your .xlsx rota. The page reads the “SHO Rota” sheet and hides weekend days automatically.

Enter daily data – For each weekday, enter the number of admissions in Admissions, and specify any Extra Team A/B/C/D doctors needed beyond the minimum. Each value must be a non‑negative integer.

Mark absences – In the Absences / Illness table (to the right of the workload inputs), tick the days on which a doctor is unavailable. Locums and PP staff are excluded from this list.

Generate – Click Generate Rota. The tool computes the weekly schedule, clerking assignments and daily messages, and displays:

Weekly Team Allocation table

Clerking Assignments table

Daily Messages section

Individual Schedules table

Print / Save PDF – Use the Print Weekly Rota button to print or save the weekly table as a PDF, or Print Individual Schedules for the per‑doctor schedule. Your browser’s print dialogue will let you select “Save as PDF”.

Customisation

The rota algorithm includes hard‑coded mappings for fixed assignments and bleeps. If your roles or bleeps change, edit the predetermined object and bleepMap in the <script> section of the HTML. The script also filters out doctors with “locum” or “pp” in their names from the absence table and individual schedules; adjust this logic if your naming conventions differ.

Dependencies

The page uses SheetJS
 (xlsx.full.min.js via CDN) to read Excel files client‑side. An internet connection is required the first time the library is fetched. After that, it may be cached by your browser. Otherwise, the application runs entirely in your browser and requires no backend server.

License

This project is provided as‑is for internal scheduling purposes. Feel free to adapt it to your rota’s needs. No warranty is expressed or implied.
