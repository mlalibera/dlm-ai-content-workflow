# Status Machine

## Estados

- new
- normalized
- context_ready
- planning
- waiting_planning_approval
- planning_approved
- copy_generation
- waiting_copy_approval
- copy_approved
- visual_generation
- qa_review
- waiting_art_approval
- revision_cycle
- approved_final
- rejected
- closed

## Estados de bloqueio

- blocked_missing_data
- blocked_retry_limit
- blocked_manual_review
- blocked_invalid_metadata