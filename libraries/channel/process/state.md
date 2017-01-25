---
layout: method
title: process::state
tags: [library]
full-name: process::state
pure-name: state
declaration: state
description: |
  This method must return the current state of the await-process. 

  If `process_state_scheduled.first` is `process_state::yield` and the timepoint `process_state_scheduled.second` is in the past, then `yield()` will be called as next action on the process. 

  If `process_state_scheduled.first` is `process_state::yield` and the timepoint `process_state_scheduled.second` is in the now or in the future, then `yield()` then a timer will be started that triggers a call to `yield()` when the timer expires.

  If `process_state_scheduled.first` is `process_state::await` and the timepoint in `process_state_scheduled.second` is in the past or now then `yield()` will be called as next action on the process. 

  If `process_state_scheduled.first` is `process_state::await` and the timepoint in `process_state_scheduled.second` is in in the future then and a timer with this timeout is started. `yield()` will be called when the timer has expired and no new value has arrived. The timer will be cancelled in the later case.
entities:
  - kind: methods
    list:
      - name: process::state
        pure-name: state
        declaration: process_state_scheduled state() const
        description: This method must return the state of the process. Subsequent calls without an intermittend `await()`, `close()` or `yield()` must return the same values. Otherwise the result is undefined.
  - kind: parameters
  - kind: result
    description: the `process_state_scheduled` state
---