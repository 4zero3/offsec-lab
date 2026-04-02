# Defense Identification – Address Consistency Failure

## Failed Control
> authoritative server-side enforcement of one coherent address state across workflow transitions

Break between:
- input validation
- backend mutation  
- preview generation
- persistence

## Defensive Weakness
1. **Fragmented Authority**: UI vs. backend standards differ
2. **No Final Revalidation**: preview survives completion
3. **Object Not Unified**: components evaluated separately
4. **Persistence Trusts Upstream**: no independent check