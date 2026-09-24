# FMCSA trucking insurance data: new-carrier timeline and feed observations

Two aggregate datasets about US motor carrier insurance filings, derived from
public FMCSA records and published by [XDate Alert](https://xdatealert.com).
No carrier-level records are included.

| File | What it measures | Live page |
|---|---|---|
| [`data/new-carrier-insurance-timeline.csv`](data/new-carrier-insurance-timeline.csv) | Share of motor carriers with a BMC-91 liability filing on file, by days since their operating-authority application (new authority and reinstatement) | [New carrier insurance timeline](https://xdatealert.com/data/new-carrier-insurance-timeline) |
| [`data/fmcsa-insurance-feed-observations.csv`](data/fmcsa-insurance-feed-observations.csv) | Daily count of forward-dated cancellation filings visible in the FMCSA MOTUS insurance feed, and how many were new that day | [FMCSA insurance feed status](https://xdatealert.com/data/fmcsa-insurance-feed-status) |

Both files are refreshed daily by a GitHub Action, so the commit history of
this repository is itself a dated archive of each day's measurement.

## Sources

- FMCSA MOTUS datasets on [data.transportation.gov](https://data.transportation.gov):
  AuthHist (`yu5v-wbh6`), Carrier (`inys-ebih`), InsHist (`3uet-3z4i`).
- Federal rule that makes cancellations public in advance:
  [49 CFR 387.313](https://www.ecfr.gov/current/title-49/subtitle-B/chapter-III/subchapter-B/part-387/subpart-C/section-387.313).

## Method and limits (timeline)

- Cross-sectional, not longitudinal: each row is today's population of
  carriers of that age, not one cohort followed over time.
- Measures filings, not the day a policy was sold. A carrier that bound
  coverage yesterday may not show as insured until the filing lands.
- Motor carriers only. Brokers and freight forwarders post a surety bond
  instead of liability insurance and would never show as insured.
- Population is the carriers XDate Alert covers: excludes CA, OR, VT and CT,
  carriers without a corporate entity name, and carriers without a phone
  number on file.

## Method and limits (feed observations)

- Observed once or more per day, shortly after 18:00 UTC. Days with several
  runs have several rows.
- On 4 August 2026 FMCSA rebuilt the MOTUS insurance datasets and the
  forward-dated count fell from roughly 1,300 to 106 overnight. The series
  shows it; the feed's own metadata did not.

## License and citation

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Cite as:

> XDate Alert (2026). FMCSA trucking insurance data: new-carrier timeline and
> feed observations. https://xdatealert.com/data/new-carrier-insurance-timeline

Not affiliated with FMCSA or any insurer.
