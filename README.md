# exocomet_hunt_TESS_results

Output from https://github.com/garethjones210/exocomet_hunt code run on entire TESS dataset (results here excluded full frame image results).

Output format is a table in text format, designed to be analysed with command line tools (e.g. grep, awk). Opening in spreadsheet software also works. The data is split into separate sectors, as collected by TESS. Any files which include _rm_ within the name have had the data between the days mentioned for re-analysis (for example, file sector_4_results_rm_1421_1424 has had data removed between days of 1421 and 1424) due to bad or flared data at these times, leading to many false postives around the same time.

Columns in table are:

(1) Light curve file name, containing Kepler ID and date.

(2) Transit signal strength, as determined by box fit test statistic.

(3) Signal to noise of the detection.

(4) Kepler date of the detected event.

(5) Asymmetry of the event.

The next two columns are parameters from the asymmetric comet curve fit:

(6) Transit entry scale length.

(7) Transit exit scale length.

Two columns of box fit parameters:

(8) Box width, giving estimate for transit width.

(9) Box depth, giving estimate for transit depth.

Finally, (10) performs some very basic classification of events, to remove common artefacts. There are four possible values here:

  point - Event is 1-2 data points wide, probably an error (e.g. cosmic ray), and too short for meaningful shape analysis.

  end - Event occurs at the end of a light curve. This is typically due to small errors in removing periodic signals in some very variable light curves, such as those from red giant stars.

  artefact - Event occurs directly after segment of missing data. These may be artefacts from PDC fitting, so analysis of raw flux is required to categorise these events.

  maybeTransit - Event not ruled out as transit by any of the above filters.

Also included is an example awk script for filtering.
