# Legitimate Interest Assessment — MapMyVisitors

**Controller**: Keshawn White
**Site**: https://maplecheeze.github.io/Portfolio/
**Processor**: MapMyVisitors (mapmyvisitors.com)
**Date of assessment**: 2026-05-12
**Lawful basis claimed**: GDPR Article 6(1)(f), Legitimate Interest

This document is kept locally for record. It is not published on the site.

## 1. Purpose test

**Legitimate interest claimed**: understanding whether the portfolio is reaching its intended audience, and roughly which regions visitors are coming from, so I can judge whether the work and outreach behind the site is having effect.

The portfolio exists to share security and privacy work and to be reachable for professional connection. Geographic awareness of who is visiting informs whether that audience is being reached.

The interest is non-commercial. No advertising, no monetization, no profiling, no behavioral targeting, no resale of data.

## 2. Necessity test

The processing collects only what is needed to derive an approximate location and basic visit context:

- IP address (used to derive geolocation, then retained by the processor per their policy)
- Approximate geolocation (country / region / city)
- Browser and OS information
- Page URL and referrer
- Visit timestamp

No fingerprinting, no cookies on the visitor's device, no tracking across other sites, no identification of individuals.

Alternatives considered:
- GitHub's built-in traffic insights: no geographic data, insufficient for the stated purpose
- Cloudflare Web Analytics: free and lower-risk, but requires domain ownership the GitHub Pages subdomain does not provide
- Plausible / Fathom: would meet the purpose but are paid services for a non-commercial portfolio

The MapMyVisitors widget is necessary in the sense that it is the available, no-cost option that satisfies the stated purpose without setting cookies on the visitor's device.

## 3. Balancing test

Factors weighing in favor of the data subject's rights:

- The data includes IP address, which is personal data under GDPR
- Visitors have no choice presented to them before the data is collected
- Data is retained by the processor for the duration of the controller's account, which could be years

Factors weighing in favor of the controller's interest:

- No special category data is processed
- No profiling, behavioral inference, or commercial use of the data
- No cross-site tracking; data is collected only in the context of this site
- No cookies are set on the visitor's device
- The processor's servers are located in the EU; no cross-border transfer concern by default
- Visitors are informed via the `/privacy/` page linked from the site footer (transparency under Art. 13)
- Visitors can object at any time via the contact listed on the privacy page (Art. 21)
- The processing is minimally invasive: a single approximate-location lookup per visit

**Conclusion**: the processing is proportionate to the stated interest. The visitor's reasonable expectations are not exceeded: aggregate site analytics for a personal portfolio is a common and well-understood use of website data. The transparency notice and right to object are sufficient safeguards.

## 4. Safeguards in place

- Privacy notice published at `/privacy/`, linked from the footer of every page
- Right-to-object contact: keshawnwhite38@gmail.com
- Processor's servers located in the EU
- No cookies set on the visitor's device by the widget
- The visitor map is hidden visually on the site (`display:none`), so visitor locations are not displayed publicly to other visitors
- DPA requested from MapMyVisitors (Art. 28)

## 5. Review

This assessment should be revisited if:

- MapMyVisitors materially changes their data handling (retention, server location, processing scope)
- The portfolio's purpose changes (e.g., adds commercial features, advertising)
- Visitor volume scales beyond personal portfolio levels
- EDPB or relevant DPA guidance changes the assessment of pixel-based analytics

Next scheduled review: 2027-05-12
