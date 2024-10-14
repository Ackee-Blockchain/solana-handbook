## Slots

A slot is a **400 milliseconds** long time interval, during which a specific validator, known as the leader, is given a chance to propose a new block. This block contains transactions that are ready to be processed within the network. After the block is proposed, other validators review and confirm its validity.

!!! note

    If a leader fails to propose a block during their assigned slot, the network moves on to the next validator in line.

## Epochs

An epoch is a fixed time period lasting approximately **432,000 slots** (about 2 days). Epochs serve as a fundamental unit of time in Solana's ecosystem. They are used to manage stake activations and deactivations, and most importantly, to determine the schedule for leader rotation. At the beginning of each epoch, the network recalculates validator stakes and updates the leader schedule for the upcoming period.

!!! info

    The probability of a given validator being chosen as a leader is proportional to their stake in the network.
