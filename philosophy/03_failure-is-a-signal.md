# Failure Is a Signal

We measure **response deviations** against established baselines.

Clean 200 responses confirm expectations.  
Failures expose internal logic.

## Metrics

- size differences (content length)
- word and line count variations
- status code patterns
- redirect chain behavior
- timing differences
- structural changes in responses

Different failures are not random noise.  
They represent different handling paths inside the system.

## Method

Baseline first, then filter.

```bash
ffuf -u URL -w list -fs 4605 -fc 404,403 -fl 10 -fw 50

##Interpretation
uniform responses → baseline behavior
-deviation → signal
-reproducible deviation → valid finding candidate
Core Principle: Different failure = different logic.