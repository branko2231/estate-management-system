# Future Migration to Microsoft 365 / SharePoint

**Planning guide for migrating the Belgravia Estate Management System from local files to Microsoft 365.**

| Field | Detail |
|---|---|
| Document Number | BEM-ROOT-003 |
| Version | 1.0 |
| Author | Branko Sevic, Estate Manager |
| Date Created | 06 July 2026 |
| Last Updated | 06 July 2026 |
| Next Review | 06 January 2027 |
| Confidentiality Level | Estate Manager Only |

---

## 1. Purpose

This system is intentionally built to migrate cleanly into Microsoft 365 (SharePoint Online, Teams, Lists and OneDrive) with no restructuring. This document explains how that migration will be carried out when the estate is ready. It is a plan, not an instruction to migrate now — the system runs fully offline today.

## 2. Why the local structure migrates cleanly

| Design choice | Migration benefit |
|---|---|
| Numbered top-level folders (00–12) | Map directly to SharePoint document libraries or folders; sort order is preserved |
| Markdown documents | Convert to Word (.docx) or paste into SharePoint pages without restructuring |
| CSV data files | Import directly into Microsoft Lists or Excel with headers intact |
| Consistent document control block | Becomes SharePoint metadata columns (Doc No., Version, Author, Review Date, Confidentiality) |
| Confidentiality levels already defined | Map to SharePoint permission groups and sensitivity labels |

## 3. Target architecture

**SharePoint site:** *Belgravia Estate Management*

| Local folder | SharePoint destination | Type |
|---|---|---|
| 00 Estate Manager (Private) | Document library — restricted | Library |
| 01 Operations | Document library + Lists | Library / List |
| 02 Staff | Document library — restricted | Library |
| 03 Property | Document library + Lists | Library / List |
| 04 Projects | Document library + Planner | Library / Planner |
| 05 Contractors | Microsoft List | List |
| 06 Vehicles | Document library + List | Library / List |
| 07 Procurement | Microsoft List | List |
| 08 Finance (Private) | Document library — restricted | Library |
| 09 Family Information (Private) | Document library — restricted | Library |
| 10 Emergency Procedures | Document library — read-only | Library |
| 11 Templates | Site content type templates | Templates |
| 12 Archive | Records library / retention label | Library |

## 4. Which CSV files become Microsoft Lists

The following are best migrated to **Microsoft Lists** (not just Excel) because they are living registers that benefit from views, filtering and alerts:

- Maintenance Tracker
- Capital Projects Tracker
- Procurement Tracker
- Inventory Database
- Asset Register
- Vehicle Costs
- Contractor Database
- Supplier Database
- Annual Planner

**How:** In a SharePoint list, choose *New → List → From CSV*, upload the file, confirm the column types, and set default views.

## 5. Permissions mapping

| Confidentiality Level | Microsoft 365 group |
|---|---|
| Estate Manager Only | `Estate-Manager` (owner) |
| Estate Manager + Chief Butler | `Estate-Leadership` |
| Department Only | `Estate-Staff` |
| Shared Read Only | `Estate-Staff` (read) + `Estate-Leadership` |

Apply **sensitivity labels** to the two *(Private)* libraries (08 Finance, 09 Family Information) and to 00 Estate Manager.

## 6. Recommended migration sequence

1. Provision the SharePoint site and the four permission groups above.
2. Create document libraries mirroring folders 00–12.
3. Create the metadata columns (Doc No., Version, Author, Date Created, Last Updated, Next Review, Confidentiality).
4. Bulk-upload the Markdown/Word documents; populate metadata from each document's control block.
5. Import the CSV files into Microsoft Lists.
6. Recreate the Templates folder as SharePoint content types.
7. Configure the Archive library with a retention label.
8. Pilot with the Estate Manager and Chief Butler before wider staff access.

## 7. What to preserve

- The numbering scheme (00–12 and BEM-XX-NN).
- The document control block on every document.
- The four confidentiality levels.
- The distinction between *documents* (Word) and *data* (Lists/Excel).

## 8. What not to do

- Do not flatten the numbered structure.
- Do not grant blanket access to the *(Private)* libraries.
- Do not migrate before permission groups and sensitivity labels are in place.

---

*This document should be reviewed with the appointed IT partner as part of the IT Modernisation capital project (see Capital Projects Register, BEM-04-01).*
