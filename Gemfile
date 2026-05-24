source "https://rubygems.org"

gem "minimal-mistakes-jekyll"

# Pin json below 2.10 — sass-embedded 1.100.0 references JSON::Fragment,
# which was removed in json gem 2.10+. Pinning json keeps JSON::Fragment
# available so sass-embedded's native extension builds. Targets the actual
# root cause; works regardless of which sass-embedded version is resolved.
gem "json", "< 2.10"
