# Farther Data Display Standard

**Status:** Canonical
**Location:** `apps/platform-web/src/components/data-display/`
**Applies to:** All data visualization across every tool and workspace in Advisor Center

---

## Mission

All charts, graphs, tables, KPI cards, and data visualizations across Advisor Center must use the Farther Data Display Library to ensure:

- **Brand consistency** — Limestone canvas, Steel Blue accents, ABC Arizona numerals
- **Professional polish** — Premium wealth management aesthetic, never generic dashboard feel
- **Accessibility** — Proper contrast, keyboard navigation, screen reader support
- **Responsive design** — Mobile-first, graceful degradation
- **No mock data** — Real data or empty states only (see CLAUDE.md Data Integrity rule)

---

## Core Principles

1. **Use existing components** — Import from `@/components/data-display`, never recreate
2. **Follow Farther brand** — Limestone 50 canvas, Charcoal 900 text, Steel Blue 700 brand lock
3. **ABC Arizona for numerals** — Large values, KPI cards, chart titles
4. **Fakt Pro for UI** — Labels, axis text, table headers, legends
5. **Soft rounded corners** — `borderRadius.xl` (16px) for cards, `borderRadius.lg` (12px) for rows
6. **Calm interactions** — `motion.easeWave` for all transitions, never abrupt
7. **Empty states over fake data** — Show EmptyState component when data unavailable

---

## Component Library

### Charts

#### LineChartCard

**Use for:** Time series trends (revenue over time, AUM growth, net flows)

```tsx
import { LineChartCard } from "@/components/data-display";

<LineChartCard
  title="Revenue Growth"
  eyebrow="12-month trend"
  value="$2.4M"
  valueLabel="YTD Revenue"
  data={monthlyData}
  xKey="month"
  series={[
    { key: "revenue", label: "Revenue", formatter: formatCurrency }
  ]}
  height={280}
/>
```

**Brand notes:**
- Primary line: `colors.brand.lock` (Steel Blue 700)
- Grid lines: `colors.primary.limestone[200]` with 3-8 dash pattern
- Axis labels: 11px Fakt Pro, `colors.secondary.slate[500]`
- Tooltip: Glass background with subtle border

---

#### AreaChartCard

**Use for:** Cumulative metrics, portfolio value, stacked asset allocation

```tsx
import { AreaChartCard } from "@/components/data-display";

<AreaChartCard
  title="Portfolio Value"
  subtitle="All connected accounts"
  data={dailyValues}
  xKey="date"
  series={[
    { key: "value", label: "Total Value", color: colors.brand.lock }
  ]}
/>
```

**Brand notes:**
- Fill opacity: 12% (soft, not aggressive)
- Stroke width: 2px
- Stacked areas use `defaultSeriesColors` palette

---

#### BarChartCard

**Use for:** Category comparisons (team revenue, fee schedules, account types)

```tsx
import { BarChartCard } from "@/components/data-display";

<BarChartCard
  title="Revenue by Team"
  data={teamData}
  xKey="teamName"
  series={[
    { key: "revenue", label: "Revenue", formatter: formatCurrency }
  ]}
/>
```

**Brand notes:**
- Bar radius: `[8, 8, 0, 0]` (rounded tops only)
- Hover cursor: Limestone overlay (subtle)
- Multi-series uses brand color palette in order

---

#### DonutAllocationCard

**Use for:** Portfolio allocation, asset class breakdown, fee structure

```tsx
import { DonutAllocationCard, type AllocationSlice } from "@/components/data-display";

const data: AllocationSlice[] = [
  { label: "Equities", value: 0.65, color: colors.brand.lock },
  { label: "Fixed Income", value: 0.25, color: colors.secondary.granite[500] },
  { label: "Alternatives", value: 0.10, color: colors.accent.bronze[500] }
];

<DonutAllocationCard
  title="Asset Allocation"
  data={data}
  value="$4.2M"
  valueLabel="Total AUM"
/>
```

**Brand notes:**
- Inner radius: 68%, outer radius: 86%
- Padding angle: 3px (subtle separation)
- Legend shows percentage breakdown with brand colors

---

#### SparklineStatCard

**Use for:** KPI cards with micro trends

```tsx
import { SparklineStatCard } from "@/components/data-display";

<SparklineStatCard
  title="Net Flows"
  label="This Quarter"
  value="$412K"
  delta={0.18}
  data={weeklyFlows}
  xKey="week"
  yKey="flow"
/>
```

**Brand notes:**
- Compact: 180px min height
- Sparkline: 1.7px stroke, brand lock color
- Delta badge: Aqua (positive), Pomegranate (negative)

---

### Tables

#### PremiumDataTable

**Use for:** Holdings, transactions, advisor rosters, relationship lists

```tsx
import { PremiumDataTable } from "@/components/data-display";
import type { ColumnDef } from "@tanstack/react-table";

const columns: ColumnDef<DataRow>[] = [
  {
    header: "Name",
    cell: ({ row }) => <AssetCell label={row.original.name} sublabel={row.original.category} />
  },
  {
    header: "Value",
    cell: ({ row }) => <NumericCell value={formatCurrency(row.original.value)} />
  }
];

<PremiumDataTable
  columns={columns}
  data={rows}
  emptyTitle="No data connected"
  emptyDescription="Holdings will appear here once portfolio data is synced."
  searchPlaceholder="Search holdings"
/>
```

**Brand notes:**
- Header: 0.68rem Fakt Pro 800, uppercase, 0.1em letter spacing, subtle color
- Row hover: Limestone overlay with 160ms ease-wave transition
- Border: Subtle Limestone between rows (58% opacity)
- Search: Pill-shaped input with glass background

---

#### Specialized Tables

Pre-built table components for common patterns:

- **HoldingsTable** — Asset cell + value + weight + day change + total return
- **TransactionsTable** — Transaction type + date + amount + quantity
- **AllocationTable** — Sleeve + value + actual % + target % + drift

```tsx
import { HoldingsTable, TransactionsTable, AllocationTable } from "@/components/data-display";

<HoldingsTable data={holdings} />
<TransactionsTable data={transactions} />
<AllocationTable data={allocations} />
```

---

### Cell Components

#### AssetCell

**Use for:** Holdings, securities, advisors, relationships

```tsx
import { AssetCell } from "@/components/data-display";

<AssetCell
  label="Vanguard Total Stock"
  sublabel="Equity"
  symbol="VTI"
  logo={<img src="/logos/vti.svg" alt="" />}
/>
```

**Brand notes:**
- Icon: 38px circle, Limestone background, brand lock text
- Falls back to 2-letter initials if no logo
- Label: 800 weight (bold), heading color
- Sublabel: 0.78rem, subtle color

---

#### NumericCell

**Use for:** Currency, percentages, counts

```tsx
import { NumericCell } from "@/components/data-display";

<NumericCell
  value={formatCurrency(1234567)}
  secondary="of portfolio"
/>
```

**Brand notes:**
- Tabular nums font variant (aligned digits)
- Right-aligned
- Primary: 800 weight, heading color
- Secondary: 0.78rem, subtle color

---

#### DeltaCell

**Use for:** Changes, returns, growth rates

```tsx
import { DeltaCell } from "@/components/data-display";

<DeltaCell value={0.18} /> {/* +18.0% in Aqua */}
<DeltaCell value={-0.05} /> {/* -5.0% in Pomegranate */}
<DeltaCell value={0} /> {/* 0.0% in muted */}
```

**Brand notes:**
- Positive: Aqua 500 (`#3CC1D3`)
- Negative: Pomegranate 500 (`#CE3657`)
- Neutral: Muted text color
- Always shows sign (+/-)

---

### Utility Components

#### EmptyState

**Use for:** No data scenarios (NEVER use mock data instead)

```tsx
import { EmptyState } from "@/components/data-display";

<EmptyState
  title="No holdings connected"
  description="Portfolio holdings will appear here once account data is synced."
/>
```

---

#### LoadingState

**Use for:** Data loading (skeleton animation)

```tsx
import { LoadingState } from "@/components/data-display";

<LoadingState rows={5} />
```

**Brand notes:**
- Limestone shimmer animation (1.4s infinite)
- Staggered widths (96%, 89%, 82%, 75%, 68%)

---

#### TableToolbar

**Use for:** Search and actions above tables

```tsx
import { TableToolbar } from "@/components/data-display";

<TableToolbar
  onSearch={(value) => setFilter(value)}
  searchPlaceholder="Search accounts"
  actions={
    <>
      <button>Export CSV</button>
      <button>Add Filter</button>
    </>
  }
/>
```

---

## Color Palette

### Primary

- **Charcoal 900** (`#333333`) — Primary text, headings, dark sections
- **Limestone 50** (`#F8F4F0`) — Default canvas
- **Limestone 200** (`#E3D3C5`) — Subtle borders, grid lines
- **White** (`#FFFFFF`) — Card backgrounds (with 68% opacity for glass effect)

### Secondary (Brand Blues)

- **Steel Blue 700** (`#3B5A69`) — Brand lock color (primary actions, chart lines)
- **Granite 500** (`#567EA1`) — Secondary series color
- **Smalt 500** (`#557A89`) — Tertiary series color
- **Sky 500** (`#5E8AD3`) — Quaternary series color

### Accent

- **Bronze 500** (`#AB7D47`) — Reserved/warning states, special highlights
- **Aqua 500** (`#3CC1D3`) — Positive deltas, growth
- **Pomegranate 500** (`#CE3657`) — Negative deltas, declines

---

## Typography

### Font Families

```tsx
fontFamily: {
  heading: "'ABC Arizona Text', ABCArizonaText, Georgia, serif",
  sans: "'Fakt Pro', Fakt, -apple-system, BlinkMacSystemFont, sans-serif"
}
```

### Usage

- **Chart titles, KPI values, table numerals** → ABC Arizona Text (300 weight)
- **UI labels, axis text, legends, table headers** → Fakt Pro (400-800 weight)
- **Eyebrows (category labels)** → Fakt Pro 800, uppercase, 0.13em letter spacing

---

## Spacing & Layout

### Card Padding

- Header: `22px 22px 12px` (top/sides/bottom)
- Chart body: `8px 14px 18px`
- Footer: `14px 22px 18px`

### Border Radius

- **Cards:** `16px` (var(--radius-data-card))
- **Rows/inputs:** `12px` (var(--radius-data-row))
- **Pills/badges:** `9999px` (var(--radius-data-pill))

### Elevation

- **Data cards:** `elevation[2]` — subtle shadow, not heavy
- **Tooltips:** `elevation[2]` with glass background
- **Modals:** `elevation[4]` (reserved for overlays)

---

## Motion

### Timing

- **Quick:** 160ms (hover states, color changes)
- **Base:** 240ms (slides, fades)
- **Slow:** 480ms (complex transitions)

### Easing

- **Primary:** `cubic-bezier(0.22, 1, 0.36, 1)` (easeWave) — calm, natural
- **Alternative:** `cubic-bezier(0.65, 0, 0.35, 1)` (easeInOut) — symmetrical

**Usage:** Table row hover, tooltip fade-in, card expansion

---

## Formatters

Import from `@/components/data-display`:

```tsx
import {
  formatCurrency,
  formatCompactCurrency,
  formatPercent,
  formatSignedPercent,
  formatNumber,
  formatCompactNumber,
  formatDate
} from "@/components/data-display";

formatCurrency(1234567.89)         // "$1,234,567.89"
formatCompactCurrency(1234567)     // "$1.2M"
formatPercent(0.1845)              // "18.5%"
formatSignedPercent(0.0842)        // "+8.4%"
formatNumber(12345.67)             // "12,345.67"
formatCompactNumber(1234567)       // "1.2M"
formatDate("2026-04-28")           // "Apr 28, 2026"
```

---

## Default Series Colors

When using multiple series without explicit colors:

1. Steel Blue 700 (brand lock)
2. Granite 500 (secondary blue)
3. Smalt 500 (tertiary blue)
4. Bronze 500 (warm accent)
5. Sky 500 (light blue)

Cycles if more than 5 series.

---

## Anti-Patterns (Do Not Do)

❌ **Don't use Recharts default styling** — Always override with Farther tokens
❌ **Don't create custom chart wrappers** — Use existing ChartCard components
❌ **Don't hardcode colors** — Import from `theme.ts` or use CSS variables
❌ **Don't use generic placeholder data** — Use EmptyState instead (Data Integrity rule)
❌ **Don't use pure black** — Use Charcoal 900 (`#333333`)
❌ **Don't use purple** — Not in Farther brand palette
❌ **Don't add heavy shadows** — Use elevation[2] for cards, elevation[1] for subtle
❌ **Don't skip responsive breakpoints** — All tables/charts must work on mobile
❌ **Don't use different fonts** — ABC Arizona for numerals/headings, Fakt Pro for UI

---

## Accessibility

### Color Contrast

- All text meets WCAG AA (4.5:1 for body, 3:1 for large)
- Delta colors (Aqua/Pomegranate) tested against Limestone 50 background
- Never rely on color alone — use icons, labels, or patterns

### Keyboard Navigation

- Tables: Full keyboard navigation with arrow keys
- Sortable headers: Space/Enter to toggle sort
- Search inputs: Focus trap, Escape to clear

### Screen Readers

- Chart cards: Use semantic `<article>` wrapper
- Tables: Proper `<thead>`, `<tbody>`, `<th scope="col">`
- Empty states: Descriptive text, not just "No data"

---

## Migration Checklist

When building a new data display:

- [ ] Import components from `@/components/data-display`
- [ ] Use Farther color tokens from `theme.ts`
- [ ] Apply ABC Arizona Text to numerals/titles
- [ ] Apply Fakt Pro to UI labels
- [ ] Use `borderRadius.xl` for cards
- [ ] Use `motion.easeWave` for transitions
- [ ] Add EmptyState for no-data scenarios
- [ ] Test responsive behavior (mobile breakpoint: 720px)
- [ ] Verify WCAG AA contrast
- [ ] Confirm no mock/placeholder data

---

## Examples in Production

### Billing Insights Pages

- `/billing/my-practice` — KPI cards + trend charts
- `/billing/teams` — Team roster table
- `/billing/relationships` — Relationship breakdown
- `/billing/fees` — Fee analysis charts
- `/billing/net-flows` — Flow trends

### Wealth Tools (Planned)

- `/wealth-tools/portfolio-analysis` — Holdings table + allocation donut
- `/wealth-tools/performance` — LineChartCard for returns
- `/wealth-tools/cash-flow` — BarChartCard for income/expenses

---

## Maintenance

### When to Update This Standard

- New chart type added to library
- Brand color palette changes
- Typography scale adjusted
- Accessibility requirements updated
- New motion pattern introduced

### Sync Requirements

Per CLAUDE.md:

> When you change platform policy, security, coding conventions, migration rules, **brand rules**, or post-task / deploy workflow, update **all** of AGENTS.md, agent.md, CLAUDE.md, the relevant .cursor/rules/ files, and docs/AGENT_SYNC.md together.

---

## Quick Reference

```tsx
// Chart
import { LineChartCard, AreaChartCard, BarChartCard, DonutAllocationCard, SparklineStatCard } from "@/components/data-display";

// Table
import { PremiumDataTable, HoldingsTable, TransactionsTable, AllocationTable } from "@/components/data-display";

// Cells
import { AssetCell, NumericCell, DeltaCell } from "@/components/data-display";

// Utility
import { EmptyState, LoadingState, TableToolbar } from "@/components/data-display";

// Formatters
import { formatCurrency, formatPercent, formatSignedPercent, formatNumber, formatDate } from "@/components/data-display";

// Theme
import { colors, typography, spacing, borderRadius, elevation, motion } from "@/lib/theme";
```

---

**End of Standard** — This is the canonical reference for all data display across Advisor Center.
