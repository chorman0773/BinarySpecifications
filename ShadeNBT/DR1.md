# Defect Report and Errata - 1

Date Applied: 2021-03-21

The following changes were applied retroactively to previously published versions of ShadeNBT:
* In versions 1.0, 1.1, 1.2, 1.3, and 1.4, the 2^24 limit on lists and compounds (in 1.4 arrays and compounds), was changed to apply to lists, arrays, and compounds.
* In version 1.4, the implementation limit applying to `TAG_Ref` were removed as `TAG_Ref` was not included in the published version. 