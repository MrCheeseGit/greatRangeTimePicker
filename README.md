# Great Range Time Picker (Wappler App Connect)

**Date and time range picker** for bookings, events, and availability: start/end date and time fields, dual calendar, and popover portaled to `document.body` so it is not clipped inside modals.

[![License: Mr Cheese Extension v1.0](https://img.shields.io/badge/License-Mr%20Cheese%20Extension%20v1.0-blue.svg)](https://www.mrcheese.co.uk/extension-license)
![Wappler](https://img.shields.io/badge/Wappler-App%20Connect-teal)
![Version](https://img.shields.io/badge/version-0%2E1%2E0-green)

Built by **[Mr Cheese](https://www.mrcheese.co.uk)** · Wappler extensions

**Related:** [Great Range Picker](https://github.com/MrCheeseGit/greatRangePicker) is the date-only sibling for report filters and dashboards (presets on by default). Use **Great Range Time Picker** when you need start/end times.

---

## What it does

| Feature | Description |
|---------|-------------|
| **Date + time** | Four fields: start date, start time, end date, end time (`HH:MM`, 24-hour) |
| **Default times** | `00:00` / `23:59` when times are left empty |
| **Time step** | Configurable native time input step (default 15 minutes) |
| **Optional presets** | Sidebar off by default; enable for report-style filters |
| **Blocked dates** | Bind unavailable days; disabled in the calendar |
| **Dual calendar** | Two months, range highlight, Escape to close |
| **Modal-safe** | Popover moves to `document.body`; centres inside Bootstrap modal dialogs |
| **Wappler-native** | `dmx-great-range-time-picker` with `data.dateFrom`, `data.timeFrom`, etc. |

---

## Requirements

- Wappler **Node.js** project with **App Connect**
- **Font Awesome** on the layout (chevron icons on trigger and month nav)
- Bootstrap 5 theme (component uses `btn`, `btn-primary`, `btn-link`)

---

## Installation

Official Wappler guide: [How To Install Custom Wappler Extensions](https://docs.wappler.io/t/how-to-install-custom-wappler-extensions/49982/).

| Path | |
|------|--|
| **npm** | Wappler Project Settings → Extensions (`wappler-great-range-time-picker`) |
| **Git** | [Extension Installer](https://www.mrcheese.co.uk/extensions/install) or manual copy below |

Git manual copy installs into `extensions/` and `public/`.

### Git install — Extension Installer (recommended)

This repo ships **`wappler-install.json`**. Use the [Mr Cheese Extension Installer](https://www.mrcheese.co.uk/extensions/install), select **Great Range Time Picker**, choose **App Connect**, and run the generated script in your project folder.

### Manual install (Git)

Run from your **Wappler project root**; skip `git clone` if you already cloned this repo alongside your project:

```bash
git clone https://github.com/MrCheeseGit/greatRangeTimePicker.git ../greatRangeTimePicker

cp ../greatRangeTimePicker/app_connect/components.hjson extensions/app_connect/components/great_range_time_picker_components.hjson
cp ../greatRangeTimePicker/includes/dmx-great-range-time-picker.js public/js/
cp ../greatRangeTimePicker/includes/dmx-great-range-time-picker.css public/css/
```

**Quit Wappler completely** and reopen your project.

### npm install (Wappler Project Settings)

1. **Wappler** → Project Settings → Extensions → Add → `wappler-great-range-time-picker`
2. From your project root: `npm install`
3. Run **Project Updater → Update** when prompted.
4. **Quit Wappler completely** and reopen your project.

#### Local `file:` development (optional)

```json
"devDependencies": {
  "wappler-great-range-time-picker": "file:../path/to/this-extension"
}
```

After you change extension source, run `npm install` again, then Project Updater if needed, and restart Wappler.

---

## Usage

### App Connect component

Set **Start date**, **End date**, **Start time**, and **End time** explicitly for bookings, or leave dates empty to use **Default date range** (`custom` uses today through +7 days when unset).

**Show preset sidebar** defaults to off. Turn it on only when you want report-style quick ranges.

```html
<dmx-great-range-time-picker
  id="bookingRange"
  date-from="2026-08-24"
  date-to="2026-08-26"
  time-from="09:00"
  time-to="17:00"
  default-time-from="09:00"
  default-time-to="17:00"
  time-step="900"
  display-format="DD/MM/YYYY"
  color-scheme="light"
  placement="modal"
  dmx-on:changed="console.log($event.detail)"
></dmx-great-range-time-picker>
```

Bindings: `{{bookingRange.data.dateFrom}}`, `{{bookingRange.data.timeFrom}}`, `{{bookingRange.data.dateTo}}`, `{{bookingRange.data.timeTo}}`.

The `changed` event detail includes `dateFrom`, `dateTo`, `timeFrom`, `timeTo`, and `preset`.

### JavaScript API

```javascript
var api = window.GREAT_RANGE_TIME_PICKER;
var instance = api.mount(hostElement, {
  dateFrom: '2026-08-24',
  dateTo: '2026-08-26',
  timeFrom: '09:00',
  timeTo: '17:00',
  showPresets: false,
  onChange: function (payload) { console.log(payload); }
});
```

---

## Compatibility

Standalone App Connect extension. Pair with [Great Range Picker](https://github.com/MrCheeseGit/greatRangePicker) only when a project needs both date-only filters and datetime booking pickers.

See the [Wappler Extension Compatibility](https://github.com/MrCheeseGit/Wappler-Extension-Docs/blob/main/extension-compatibility.md) guide for install notes and troubleshooting.

---

## License

[Mr Cheese Extension License v1.0](https://www.mrcheese.co.uk/extension-license). See [LICENSE](LICENSE).
