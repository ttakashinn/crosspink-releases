# Third-party notices for CrossPink firmware

This repository distributes firmware and documentation separately from development history. The root MIT license applies to the original CrossPoint code under that license; it does **not** relicense every component in the linked firmware.

## Components reviewed

| Component | Evidence in the build/source tree | License / distribution requirement |
| --- | --- | --- |
| CrossPoint / CrossPink base | Root `LICENSE` | MIT; retain copyright and permission notice. |
| FreeInk SDK and Open X4-derived display work | `freeink-sdk/LICENSE`, `freeink-sdk/NOTICE` | MIT; preserve both notices. |
| Arduino-wolfSSL 5.7.2 | Package `COPYING`, `library.json`, headers such as `src/src/tls.c`; linked through FreeInk SecureNet | Package metadata says GPL-2.0-only; several source headers say GPL-2.0-or-later. Both require applicable source availability when distributing the linked work. No separate commercial grant has been established for this distribution. The metadata/header difference must not be interpreted as permission to close the source. |
| WebSockets 2.7.3 | Package `LICENSE`, `library.json`; `CrossPointWebServer` | LGPL-2.1; library source and relinking obligations apply. |
| Arduino ESP32 3.3.7 | Framework `package.json`, core source headers | LGPL-2.1-or-later; notices, source and applicable relinking obligations remain. |
| ESP-IDF and included components | Framework `LICENSE` and component notices | Apache-2.0, BSD, MIT and component-specific terms, including Espressif binary library redistribution terms. |
| ArduinoJson 7.4.2, QRCode 0.0.1, SdFat | Resolved package license files | MIT; retain notices. |
| PNGdec 1.1.6 and JPEGDEC pinned revision | Resolved package `LICENSE` | Apache-2.0; retain copyright/license and describe modifications where applicable. CrossPink applies build compatibility patches in the corresponding source. |
| Expat, miniz and uzlib | Vendored notices in `lib/` | MIT / permissive notices as reproduced in `licenses/`. |
| Lucide / Feather icons | SDK icon license and dashboard icon license | ISC / MIT; retain authorship and license notices. |
| Embedded fonts | Each family’s `OFL.txt` or `UFL.txt` | SIL Open Font License or Ubuntu Font Licence. The text for each supplied family is included separately. Older downloadable font packs also contain their own notices. |
| JSZip and bundled pako | Header in the served `jszip.min.js` | JSZip MIT or GPLv3; MIT option and pako MIT/zlib notices are reproduced. |

The license texts in [licenses/](licenses/) are copied from the actual checked-out/resolved dependencies or their pinned upstream versions. [License inventory](licenses/INDEX.md) identifies their origins. Different historical firmware versions can use different revisions. This inventory is not a statement that a MIT-only or source-free redistribution has been cleared.

## Corresponding source

The application and SDK repositories are currently private. This release repository contains documentation and license texts; its automatically generated source archives do not contain firmware source. Earlier release notes may contain source links that are no longer publicly accessible. Repository visibility does not alter the component licenses or their distribution requirements.

Free-of-charge sharing, including to a small community group, is still distribution. Providing license text alone does not replace GPL corresponding source or LGPL relinking requirements. Any future private-source distribution needs a resolved license/source distribution arrangement before public firmware publication. No restriction on the rights granted by the component licenses is added here.

See the [GNU GPL FAQ](https://www.gnu.org/licenses/gpl-faq.en.html), [GPLv2 FAQ](https://www.gnu.org/licenses/old-licenses/gpl-2.0-faq.en.html) and [wolfSSL licensing](https://www.wolfssl.com/license/). The currently published wolfSSL licensing page describes current releases; the package version and source headers above are the evidence for this project’s pinned 5.7.2 dependency.
