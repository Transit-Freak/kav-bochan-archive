# קוד שהועבר מהריפו הראשי

קוד מ-[kav-bochan](https://github.com/Transit-Freak/kav-bochan) שכבר לא בשימוש. הוא נשמר כאן כדי שיהיה אפשר לחזור אליו.

- **מתי:** 15.11.2026.
- **מאיפה:** `.github/workflows/` ו-`tools/` בריפו הראשי.
- **הקומיט האחרון שבו הקבצים עוד היו ב-main:**
  [`8c42c68`](https://github.com/Transit-Freak/kav-bochan/tree/8c42c685db4337d128f7b304fcaac42df38e3227)
- **מה עבר:**
  - 41 workflows אל `workflows/`;
  - 21 סקריפטים שרק ה-workflows האלה הריצו;
  - 29 סקריפטים שאף קובץ לא מפנה אליהם.

  הסקריפטים נמצאים ב-`tools/`, באותם שמות. בסך הכול 8,854 שורות.

## חשוב

- קבצי ה-workflow נמצאים ב-`retired-code/workflows/` ולא ב-`.github/workflows/`, ולכן **הם לא רצים כאן**. לא להעביר אותם לשם.
- לפני ההעברה בדקנו שאף קובץ שנשאר בריפו הראשי לא מפנה לקבצים האלה: לא בשם קובץ, לא ב-import, ולא דרך `workflow_run`.

## איך משחזרים

1. מעתיקים את הקובץ חזרה לאותו מקום בריפו הראשי:
   - `workflows/X.yml` חוזר אל `.github/workflows/X.yml`;
   - `tools/X` חוזר אל `tools/X`.
2. לחלופין, לוקחים אותו מהקומיט האחרון:
   `git show 8c42c685db4337d128f7b304fcaac42df38e3227:tools/X`

   ההיסטוריה המלאה של כל קובץ נשארת ב-git של הריפו הראשי.
3. אם הסקריפט מייבא סקריפט אחר מ-`tools/`, צריך לוודא שגם הוא קיים.

## מה הועבר ולמה

הראיה ל-workflow: לא רץ מעל 60 יום, נכון ל-15.11.2026. הוא הופעל רק ידנית או בדחיפה לנתיב שלו, ואף workflow אחר לא תלוי בו.

### גישושים (probe-*)

בדיקות חד-פעמיות של מקורות נתונים. קיבלו תשובה ולא הופעלו מאז.

| workflow | ריצה אחרונה | ריצות בסך הכול | סקריפטים שהועברו איתו |
|---|---|---|---|
| `probe-ckan.yml` | 2026-09-06 | 1 | `probe_ckan.py` |
| `probe-databus-bulk.yml` | 2026-09-06 | 5 | `probe_ride_stops.py` |
| `probe-fare-zones.yml` | 2026-08-29 | 15 | `build_fare_zones.py`, `probe_fare_zone_src.py` |
| `probe-fill-removed.yml` | 2026-07-28 | 2 | — |
| `probe-gis.yml` | 2026-09-01 | 5 | — |
| `probe-gov-sources.yml` | 2026-07-28 | 14 | `probe_gov_sources.py` |
| `probe-govmap.yml` | 2026-09-01 | 5 | — |
| `probe-gtfs-archives.yml` | 2026-07-28 | 6 | `probe_gtfs_archives.py` |
| `probe-holidays.yml` | 2026-09-07 | 2 | — |
| `probe-link.yml` | 2026-09-01 | 1 | — |
| `probe-mapillary-il.yml` | 2026-09-01 | 2 | — |
| `probe-mot-datasets.yml` | 2026-09-06 | 1 | `probe_mot_datasets.py` |
| `probe-open-imagery.yml` | 2026-09-01 | 3 | — |
| `probe-osm-provenance.yml` | 2026-09-01 | 1 | — |
| `probe-osrm-shape.yml` | 2026-09-02 | 1 | `osrm_shape_probe.py` |
| `probe-peri-zone.yml` | 2026-08-29 | 11 | `probe_peri_zone.py` |
| `probe-publisher.yml` | 2026-08-31 | 73 | — |
| `probe-realtime.yml` | 2026-07-28 | 12 | — |
| `probe-shelters.yml` | 2026-09-01 | 1 | — |
| `probe-siri-gtfs.yml` | 2026-09-06 | 2 | `probe_siri_gtfs.py` |
| `probe-siri-raw.yml` | 2026-09-06 | 1 | — |
| `probe-terms.yml` | 2026-09-01 | 1 | — |
| `probe-tlv-terms.yml` | 2026-09-01 | 4 | — |
| `probe-transitfeeds.yml` | 2026-08-23 | 6 | `probe_hadar.py` |
| `probe-variant-stop.yml` | 2026-09-02 | 1 | `probe_variant_stop.py` |
| `probe-w3form.yml` | 2026-08-29 | 11 | `probe_w3form.py` |

### סריקות

סריקות ארכיון חד-פעמיות. התוצאות כבר במאגר.

| workflow | ריצה אחרונה | ריצות בסך הכול | סקריפטים שהועברו איתו |
|---|---|---|---|
| `geo-scan.yml` | 2026-08-06 | 6 | — |
| `geo2-scan.yml` | 2026-08-06 | 6 | `backfill_geo_before.py` |
| `geo3-scan.yml` | 2026-08-08 | 106 | `backfill_geo_truth.py` |
| `freq-scan.yml` | 2026-08-06 | 39 | — |
| `enrich-scan.yml` | 2026-08-06 | 34 | — |
| `magihim-scan.yml` | 2026-08-01 | 4 | `magihim_scraper.py` |
| `routes-scan.yml` | 2026-08-03 | 9 | `backfill_routes_daily.py` |

### מילויים (backfill)

מילויים חד-פעמיים שהסתיימו.

| workflow | ריצה אחרונה | ריצות בסך הכול | סקריפטים שהועברו איתו |
|---|---|---|---|
| `backfill-planned.yml` | 2026-09-03 | 43 | — |
| `backfill-platforms.yml` | 2026-09-03 | 11 | — |
| `backfill-platform-rows.yml` | לא רץ אף פעם | 0 | — |
| `backfill-rem-codes.yml` | 2026-08-18 | 2 | `backfill_rem_codes.py` |
| `tf-backfill.yml` | 2026-08-09 | 81 | `fix_stop_blips.py`, `mark_archive_removed.py`, `merge_line_conflicts.py` |
| `rishui-backfill.yml` | 2026-09-07 | 9 | — |

### אחרים

pubdest-hist: מושבת ידנית מאז 31.08. fleet-probe: גישוש חד-פעמי.

| workflow | ריצה אחרונה | ריצות בסך הכול | סקריפטים שהועברו איתו |
|---|---|---|---|
| `pubdest-hist.yml` | 2026-08-31 | 9 | — |
| `fleet-probe.yml` | 2026-08-18 | 2 | — |

### סקריפטים יתומים

אף workflow, סקריפט, בדיקה או מסמך בריפו הראשי לא מפנה אליהם. ברובם תיקונים, מילויים וגישושים חד-פעמיים מאוגוסט–אוקטובר 2026.

| סקריפט | הקומיט האחרון שנגע בו בריפו הראשי |
|---|---|
| `GTFS-MOT-NOTES.md` | 2026-09-07: הקו בזמן: רציפים אמיתיים — בקובץ התחנות של המשרד יש שורה לכל רציף באות |
| `anchor_2017.py` | 2026-08-07: הקו בזמן — עוגני 2017 (#108) |
| `audit_state_gaps.py` | 2026-08-25: ביקורת ארצית: שחזור 258 אירועי מסלול שהסריקה בלעה + הקשחת ההשוואה |
| `backfill_mode_ob.py` | 2026-08-10: היסטוריית התחנות של 2023–2026 נבנתה מחדש מהקבצים הגולמיים |
| `backfill_stops_gtfs.py` | 2026-08-10: כתיבה אטומית ושמירה לפי שעון בסריקת התחנות מהקבצים הגולמיים |
| `backfill_stops_obus.py` | 2026-10-10: קו בזמן: שינויי תחנות 2015–2017 באותו עיצוב כמו שאר השנים (#215) |
| `backfill_wa.py` | 2026-08-20: הקו בזמן: השלמת דגל הנגישות ל-5,284 קווים שהקובץ שלהם לא נכתב מאז התיק |
| `bootstrap_modes.py` | 2026-08-08: רכבת ומוניות שירות — שתי קטגוריות נפרדות, ושינוי סוג קו כאירוע |
| `build_early_rail_stations.py` | 2026-09-26: רכבת 2013–2014: בלחיצה על נסיעה — מפה ורשימת תחנות (בלי זמנים), מיקומי |
| `build_historical_groups_2012.py` | 2026-09-25: Build conservative display-only historical route groups from 2012 GTFS |
| `drop_premature_mode.py` | 2026-08-10: היסטוריית התחנות של 2023–2026 נבנתה מחדש מהקבצים הגולמיים |
| `enrich_missing_stop_codes.py` | 2026-08-18: הקו בזמן: תחנה שירדה שאינה בקובץ הקו מצוירת עכשיו במפה |
| `fill_stop_lines.py` | 2026-08-09: קווים שעצרו בתחנה — גם באירועים מהארכיון |
| `fix_late_new.py` | 2026-08-10: היסטוריה של ארבע וחצי שנים לרכבת, לרכבת הקלה ולמוניות השירות |
| `fix_stop_move_from.py` | 2026-08-09: הזזת תחנה בלי המיקום שממנו · הצלבת מגיעים 2012 עם היסטוריית התחנות |
| `fix_tt_event_precision.py` | 2026-08-10: מסלולים ל-521 וריאנטים שהיו בלי מפה, ומפה גם לתיעוד הראשון והאחרון |
| `flag_unserved_stops.py` | 2026-08-09: הזזת תחנה בלי המיקום שממנו · הצלבת מגיעים 2012 עם היסטוריית התחנות |
| `mark_stop_event_flags.py` | 2026-08-09: טאב התחנות: 4.5 מגה בכניסה הפכו לעשרות קילובייט |
| `merge_rebuilt_archive.py` | 2026-08-10: הארכיון נבנה מחדש — 12,392 אירועים שלא קרו ירדו |
| `probe_govmap.py` | 2026-08-17: מחירון: בדיקת GovMap (מרשם הכתובות הארצי) כמקור חיפוש כתובות |
| `probe_tf_early.py` | 2026-08-08: תשובה על עומק הארכיון: 16.3.2017 הוא הרצפה |
| `repair_early_notrips.py` | 2026-09-26: ארכיון אוטובוס פתוח: צילום שבו הקו רשום בלי אף נסיעה סומן בטעות 'תחנות |
| `repair_swapped_shapes.py` | 2026-09-26: שרטוטי 2012: נקודות עם קו רוחב/אורך הפוכים (הקו 'קפץ' לים) — מתוקנות ב |
| `run_backfill_tf.sh` | 2026-08-08: מפקח על ריצת המילוי: החזרה אוטומטית אחרי נפילת רשת |
| `scan_seen_ob.py` | 2026-08-10: היסטוריית התחנות של 2023–2026 נבנתה מחדש מהקבצים הגולמיים |
| `strip_stop_range.py` | 2026-08-10: כלי לפינוי טווח תאריכים בהיסטוריית התחנות |
| `strip_tf_events.py` | 2026-08-09: כלי למחיקת אירועי הארכיון לקראת בנייה מחדש |
| `sweep_line_pages.mjs` | 2026-08-10: סריקת כל 13,189 עמודי הקווים, וכתובת של קו נקראת גם אחרי הטעינה |
| `taxi_archaeology.py` | 2026-08-23: taxi_archaeology: HEAD לפני כל צילום — תאריך חסר לא מפיל את הסריקה |

## סבב 2 (15.11.2026)

- **הקומיט האחרון ב-main שבו הקבצים עוד היו:**
  [`a7bc736`](https://github.com/Transit-Freak/kav-bochan/tree/a7bc736d168114966a32e3f934964cf4286ad8e0)
- **שחזור:** `git show a7bc736d168114966a32e3f934964cf4286ad8e0:tools/X`
- **מה עבר:** 3 workflows ו-6 סקריפטים, כ-1,400 שורות. לכל אחד מהם יש אישור של שלמה.

| קובץ | למה הועבר |
|---|---|
| `workflows/sakachot-pilot.yml` + `tools/sakachot_pilot.py` | פיילוט חד-פעמי. רץ לאחרונה ב-01.09 |
| `workflows/bitzua-survey.yml` + `tools/bitzua_survey.py` | סקר להפעלה ידנית שלא הופעל אף פעם. כיוון שלא הופעל, לא נוצרה תיקייה `docs/surveys` |
| `workflows/compare-mot.yml` + `tools/compare_mot.py` | השוואה חד-פעמית לקובצי משרד התחבורה. רצה לאחרונה ב-06.09. התוצאות ב-`docs/compare` נשארו בריפו הראשי |
| `tools/itm.py` | אף קובץ לא מייבא אותו. יש העתקים מקומיים של המרת ITM בסקריפטים אחרים |
| `tools/taba_merge.py` | אף workflow או סקריפט לא קורא לו, גם לא `rail-tunnels.yml`. עודכן לאחרונה ב-20.09 |
| `tools/check_lh_ui.mjs` | בדיקת עשן ישנה של "הקו בזמן" שלא הייתה מחוברת לשום workflow. הבדיקות הייחודיות שלה מוזגו ל-`check_line_history_ui.mjs` בריפו הראשי (שלב ה') |
