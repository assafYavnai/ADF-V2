# PHASE-MODEL-NO-EXCEPTIONS-AND-FOLDER-BASED-BACKLOG

## CONTEXT

Review of the target phase model raised a pushback around backlog shape and backlog transition.
The earlier wording treated some current non-compliant structures as transition-era exceptions and also required a backlog `README.md` as the candidate entry surface.
That did not fit the desired governed model.
The backlog example under `phases/backlog/memory/` shows that a backlog candidate may naturally contain several different definition or context files rather than one `README.md`.
The current odd legacy backlog shape is the nested `phases/backlog/system-definition/phases/...` structure, which should be normalized rather than preserved as an exception.

## OPTIONS

- Keep allowing target-model exceptions for legacy structures and require `README.md` as the backlog entry file.
- Remove the `README.md` requirement but continue to tolerate legacy exception folders under the target model.
- Remove standing exceptions, make backlog folder-based rather than entry-file-based, and require legacy backlog normalization before target-model activation.

## DECISION

The agreed target phase-model rules are:

- no target-model structural exceptions are allowed
- current non-target structures remain part of the bootstrap runtime only until the target model is activated
- the target-model activation checkpoint must normalize each affected current structure into a governed target storage class
- backlog candidates are folder-based, not entry-file-based
- no special `README.md` file is required for a backlog candidate
- the meaning of a backlog candidate is carried by the files inside its slug folder
- backlog files may contribute phase-definition material, step-definition material, shaping notes, research, or supporting context
- backlog content may remain partial and exploratory until promotion shaping produces a compliant promoted phase
- nested legacy backlog structures such as `phases/backlog/<slug>/phases/...` must not survive target-model activation
- when a promoted phase is demoted back to backlog, its former promoted id must be preserved inside the demoted candidate content, preferably in `CONTRACT.md` when that file is kept

This decision removes the last backlog-exception path, keeps backlog flexible without a misleading `README.md` requirement, and preserves deterministic normalization for target-model activation.

## APPROVAL

EXPLICIT
