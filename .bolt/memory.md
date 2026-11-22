# Project memory

## Product intent & audience

- PWA for digital PPE (Personal Protective Equipment) delivery tracking, cost control, and instant PDF generation.
- Core entities: `trabajadores` (workers) and `sedes` (sites/locations), linked by `trabajadores.sede_id`.
- Role-based access control (RBAC) with offline sync to Supabase.
- UI language: Spanish (e.g., "Incluir sedes", section/form labels).

## Brand personality & voice

- Production-grade, professional industrial safety management tool.
- Clear, utilitarian Spanish-language copy; no playful tone.

## Visual design & UX direction

- Stack: Vite + React + TypeScript + Tailwind CSS; Lucide React for icons.
- Imports use `@/` path alias (maps to `src/`); avoid deep relative paths.
- Forms use mandatory selectors where relationships exist (e.g., worker → site).
- Inline quick-create flows: create a new entity (sede) from within a parent form (trabajador) and auto-select it.
- List/detail patterns with toggle controls for availability states.
- Responsive PWA behavior; data must persist across reloads.

## Decisions, constraints & rationale

- Supabase is the persistent backend; local state mirrors and syncs on creation.
- `sedes` table and `trabajadores.sede_id` column already exist in schema; UI now wires them.
- Sede management supports: create, view address, toggle availability.
- Both worker-form and dedicated "Incluir sedes" section can create sedes; both attempt Supabase persistence.
- Type-check, lint, and build must all pass before considering work complete.
- Do not install extra UI/icon/theme packages beyond Tailwind and Lucide React.

## Open questions & assumptions

- Assumed offline sync uses local-first storage with Supabase write-through; conflict resolution strategy not yet defined.
- Exact RBAC roles and permissions not yet specified.
- PDF generation library/approach not yet confirmed.
- Cost-control features beyond delivery tracking not yet detailed.