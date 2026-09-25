# PKUEEG preprocessed EEG

Filter band: 1-8 Hz; sampling rate: 128 Hz. NPZ arrays contain eeg_data
(channels x samples, microvolts) and ch_names; see ../npz_data_dictionary.json.
Files are organized as sub-XX/ses-dayY/eeg/sub-XX_ses-dayY_task-audio_desc-storyNN_eeg.npz.
Rest uses desc-rest. Days contain stories 01-17, 18-33 and 34-50.
The task-audio entity identifies the parent continuous recording, which includes rest.
These are custom NPZ derivatives, not a standard raw BIDS EEG file format.
The 2026-09-16 update changed locations only, not samples or preprocessing versions.
