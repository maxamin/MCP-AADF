# Autonomous experimentation engine

**Status:** design specification; not implemented.

## Scientific loop
Observation -> hypothesis -> falsifiable prediction -> proposed experiment -> policy review -> sandbox execution -> result analysis -> evidence update.

## Experiment manifest
Specify target image hash, hypothesis, independent variables, controls, permitted capabilities, budget, expected observations, stop conditions, cleanup, and evaluation rubric.

## Guardrails
The planner cannot select new targets, broaden scope, override budget or bypass approval. Experiments with uncertain side effects are denied or redirected to a disposable simulation.

## Reproducibility
Pin tool versions, OS images, seeds, environment variables and input fixtures. Save structured events, artifact hashes and failed attempts. Separate observed outcome from interpretation.

## Stopping conditions
Stop on target fingerprint change, unexpected privilege increase, evidence of sensitive data, sandbox escape indicators, resource exhaustion, or inability to verify rollback.

## Evaluation
Measure hypothesis precision, experiment reproducibility, false discoveries, cost per validated capability, and human-review workload.
