---
title: "Create Async TranscriptMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 5 requests per min per bot"
source_file: "reference/recording_create_transcript_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:01:56.445Z"
api_parameters_count: "29"
---
## POST https://us-east-1.recall.ai/api/v1/recording/{id}/create_transcript/

This endpoint is rate limited to: 5 requests per min per bot

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this recording. |
| metadata | object | No |  |
| provider | object | Yes |  |
| recording | object | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes | Download transcript for the recording. See response format here |
| download_url | uri \| null | Yes | Download transcript for the recording. See response format here |
| provider_data_download_url | uri \| null | Yes | Download raw transcription data received from the provider for the recording. See response format here |
| diarization | object \| null | Yes |  |
| use_separate_streams_when_available | boolean | Yes |  |
| assembly_ai_async | object \| null | Yes |  |
| deepgram_async | object \| null | Yes |  |
| gladia_v1_async | object \| null | Yes |  |
| gladia_v2_async | object \| null | Yes |  |
| rev_async | object \| null | Yes |  |
| speechmatics_async | object \| null | Yes |  |
| assembly_ai_async_chunked | object | No | Docs: https://www.assemblyai.com/docs/api-reference/transcripts/submit |
| assembly_ai_streaming | object | No | Docs: https://www.assemblyai.com/docs/api-reference/streaming/realtime |
| deepgram_streaming | object | No | Docs: https://developers.deepgram.com/reference/streaming |
| gladia_v1_streaming | object | No | Docs: https://docs.gladia.io/reference/live-audio |
| gladia_v2_streaming | object | No | Docs: https://docs.gladia.io/api-reference/v2/live/init |
| rev_streaming | object | No | Docs: https://docs.rev.ai/api/streaming/requests/ |
| aws_transcribe_streaming | object | No | You must specify either:  language_code(e.g en-US) OR Set language_identification to true AND specify language_options(e.g en-US,fr-FR,es-US,de-DE,it-IT).  Docs: https://docs.aws.amazon.com/transcribe/latest/APIReference/API_streaming_StartStreamTranscription.html |
| speechmatics_streaming | object | No | You must specify language (e.g en) Docs: https://docs.speechmatics.com/rt-api-ref#transcription-config |
| meeting_captions | object | No |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/recording/id/create_transcript/"
payload = {
"metadata": { "additionalProp": "string" },
"provider": {
"assembly_ai_async": {
"language": "string",
"audio_end_at": 0,
"audio_start_from": 0,
"auto_chapters": True,
"auto_highlights": True,
"boost_param": "string",
"content_safety": True,
"content_safety_confidence": 0,
"custom_topics": True,
"disfluencies": True,
"dual_channel": True,
"entity_detection": True,
"filter_profanity": True,
"format_text": True,
"iab_categories": True,
"language_code": "string",
"language_confidence_threshold": 0,
"language_detection": True,
"punctuate": True,
"redact_pii": True,
"redact_pii_audio": True,
"redact_pii_audio_quality": "string",
"redact_pii_policies": ["string"],
"redact_pii_sub": "string",
"sentiment_analysis": True,
"speaker_labels": True,
"speakers_expected": 0,
"speech_model": "string",
"speech_threshold": 0,
"summarization": True,
"summary_model": "string",
"summary_type": "string",
"topics": ["string"],
"word_boost": ["string"],
"keyterms_prompt": ["string"]
},
"deepgram_async": {
"tier": "string",
"model": "string",
"version": "string",
"language": "string",
"detect_language": True,
"punctuate": True,
"profanity_filter": True,
"redact": ["string"],
"diarize": True,
"diarize_version": "string",
"smart_format": True,
"numerals": True,
"search": ["string"],
"replace": ["string"],
"keywords": ["string"],
"keyterm": ["string"],
"filler_words": True,
"summarize": True,
"detect_topics": True,
"tag": True,
"mip_opt_out": True,
"credential_id": "string"
},
"gladia_v_async": {
"language_behaviour": "string",
"language": "string",
"toggle_noise_reduction": True,
"transcription_hint": "string",
"toggle_diarization": "string",
"toggle_direct_translate": True,
"target_translation_language": "string",
"diarization_num_speakers": 0,
"diarization_min_speakers": 0,
"diarization_max_speakers": 0
},
"gladia_v_async": {
"context_prompt": "string",
"custom_vocabulary": "string",
"custom_vocabulary_config": {
"default_intensity": 0,
"vocabulary": [
{
"value": "string",
"intensity": 0,
"pronunciations": ["string"],
"language": "string"
}
]
},
"detect_language": True,
"enable_code_switching": True,
"code_switching_config": { "languages": ["string"] },
"language": "string",
"subtitles": True,
"subtitles_config": { "formats": ["string"] },
"diarization": True,
"diarization_config": {
"number_of_speakers": 0,
"min_speakers": 0,
"max_speakers": 0
},
"translation": True,
"translation_config": {
"target_languages": ["string"],
"model": "string"
},
"summarization": True,
"summarization_config": { "type": "string" },
"moderation": True,
"named_entity_recognition": True,
"chapterization": True,
"name_consistency": True,
"custom_spelling": True,
"structured_data_extraction": True,
"sentiment_analysis": True,
"audio_to_llm": True,
"audio_to_llm_config": { "prompts": ["string"] },
"sentences": True,
"display_mode": True,
"punctuation_enhanced": True
},
"rev_async": {
"detect_language": True,
"language": "string",
"skip_diarization": True,
"skip_postprocessing": True,
"skip_punctuation": True,
"remove_disfluencies": True,
"remove_atmospherics": True,
"filter_profanity": True,
"custom_vocabulary_id": "string",
"custom_vocabularies": ["string"]
},
"speechmatics_async": {
"language": "string",
"domain": "string",
"output_locale": "string",
"operating_point": "string",
"additional_vocab": [
{
"content": "string",
"sounds_like": ["string"]
}
],
"language_identification_config": {
"expected_languages": ["string"],
"low_confidence_action": "string",
"default_language": "string"
},
"enable_entities": True
}
}
}
headers = {
"accept": "application/json",
"content-type": "application/json"
}
response = requests.post(url, json = payload, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "recording": {
    "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "metadata": {
      "additionalProp": "string"
    }
  },
  "created_at": "2025-06-10T19:01:45.628Z",
  "status": {
    "code": "processing",
    "sub_code": "string",
    "updated_at": "2025-06-10T19:01:45.628Z"
  },
  "metadata": {
    "additionalProp": "string"
  },
  "data": {
    "download_url": "string",
    "provider_data_download_url": "string"
  },
  "diarization": {
    "use_separate_streams_when_available": true
  },
  "provider": {
    "assembly_ai_async": {
      "language": "string",
      "audio_end_at": 0,
      "audio_start_from": 0,
      "auto_chapters": true,
      "auto_highlights": true,
      "boost_param": "string",
      "content_safety": true,
      "content_safety_confidence": 0,
      "custom_spelling": [
        {}
      ],
      "custom_topics": true,
      "disfluencies": true,
      "dual_channel": true,
      "entity_detection": true,
      "filter_profanity": true,
      "format_text": true,
      "iab_categories": true,
      "language_code": "string",
      "language_confidence_threshold": 0,
      "language_detection": true,
      "punctuate": true,
      "redact_pii": true,
      "redact_pii_audio": true,
      "redact_pii_audio_quality": "string",
      "redact_pii_policies": [
        "string"
      ],
      "redact_pii_sub": "string",
      "sentiment_analysis": true,
      "speaker_labels": true,
      "speakers_expected": 0,
      "speech_model": "string",
      "speech_threshold": 0,
      "summarization": true,
      "summary_model": "string",
      "summary_type": "string",
      "topics": [
        "string"
      ],
      "word_boost": [
        "string"
      ],
      "keyterms_prompt": [
        "string"
      ]
    },
    "deepgram_async": {
      "tier": "string",
      "model": "string",
      "version": "string",
      "language": "string",
      "detect_language": true,
      "punctuate": true,
      "profanity_filter": true,
      "redact": [
        "string"
      ],
      "diarize": true,
      "diarize_version": "string",
      "smart_format": true,
      "numerals": true,
      "search": [
        "string"
      ],
      "replace": [
        "string"
      ],
      "keywords": [
        "string"
      ],
      "keyterm": [
        "string"
      ],
      "filler_words": true,
      "summarize": true,
      "detect_topics": true,
      "tag": true,
      "mip_opt_out": true,
      "credential_id": "string"
    },
    "gladia_v1_async": {
      "language_behaviour": "string",
      "language": "string",
      "toggle_noise_reduction": true,
      "transcription_hint": "string",
      "toggle_diarization": "string",
      "toggle_direct_translate": true,
      "target_translation_language": "string",
      "diarization_num_speakers": 0,
      "diarization_min_speakers": 0,
      "diarization_max_speakers": 0
    },
    "gladia_v2_async": {
      "context_prompt": "string",
      "custom_vocabulary": "string",
      "custom_vocabulary_config": {
        "default_intensity": 0,
        "vocabulary": [
          {
            "value": "string",
            "intensity": 0,
            "pronunciations": [
              "string"
            ],
            "language": "string"
          }
        ]
      },
      "detect_language": true,
      "enable_code_switching": true,
      "code_switching_config": {
        "languages": [
          "string"
        ]
      },
      "language": "string",
      "subtitles": true,
      "subtitles_config": {
        "formats": [
          "string"
        ]
      },
      "diarization": true,
      "diarization_config": {
        "number_of_speakers": 0,
        "min_speakers": 0,
        "max_speakers": 0
      },
      "translation": true,
      "translation_config": {
        "target_languages": [
          "string"
        ],
        "model": "string"
      },
      "summarization": true,
      "summarization_config": {
        "type": "string"
      },
      "moderation": true,
      "named_entity_recognition": true,
      "chapterization": true,
      "name_consistency": true,
      "custom_spelling": true,
      "structured_data_extraction": true,
      "sentiment_analysis": true,
      "audio_to_llm": true,
      "audio_to_llm_config": {
        "prompts": [
          "string"
        ]
      },
      "sentences": true,
      "display_mode": true,
      "punctuation_enhanced": true
    },
    "rev_async": {
      "detect_language": true,
      "language": "string",
      "skip_diarization": true,
      "skip_postprocessing": true,
      "skip_punctuation": true,
      "remove_disfluencies": true,
      "remove_atmospherics": true,
      "filter_profanity": true,
      "custom_vocabulary_id": "string",
      "custom_vocabularies": [
        "string"
      ]
    },
    "speechmatics_async": {
      "language": "string",
      "domain": "string",
      "output_locale": "string",
      "operating_point": "string",
      "additional_vocab": [
        {
          "content": "string",
          "sounds_like": [
            "string"
          ]
        }
      ],
      "language_identification_config": {
        "expected_languages": [
          "string"
        ],
        "low_confidence_action": "string",
        "default_language": "string"
      },
      "enable_entities": true
    },
    "assembly_ai_async_chunked": {
      "boost_param": "string",
      "content_safety": true,
      "content_safety_confidence": 0,
      "custom_spelling": [
        {
          "to": "string",
          "from": [
            "string"
          ]
        }
      ],
      "disfluencies": true,
      "filter_profanity": true,
      "format_text": true,
      "language_code": "string",
      "language_confidence_threshold": 0,
      "language_detection": true,
      "punctuate": true,
      "redact_pii": true,
      "redact_pii_policies": [
        "string"
      ],
      "redact_pii_sub": "string",
      "speaker_labels": true,
      "speakers_expected": 0,
      "speech_model": "string",
      "speech_threshold": 0,
      "word_boost": [
        "string"
      ],
      "keyterms_prompt": [
        "string"
      ],
      "chunk_minimum": 180,
      "chunk_maximum": 300
    },
    "assembly_ai_streaming": {
      "word_boost": [
        "string"
      ],
      "disable_partial_transcripts": true
    },
    "deepgram_streaming": {
      "tier": "string",
      "model": "string",
      "version": "string",
      "language": "string",
      "punctuate": true,
      "filler_words": true,
      "keyterm": [
        "string"
      ],
      "profanity_filter": true,
      "redact": [
        "string"
      ],
      "diarize": true,
      "diarize_version": "string",
      "smart_format": true,
      "ner": true,
      "alternatives": 0,
      "numerals": true,
      "search": [
        "string"
      ],
      "replace": [
        "string"
      ],
      "keywords": [
        "string"
      ],
      "interim_results": true,
      "endpointing": 0,
      "log_data": true,
      "mip_opt_out": true
    },
    "gladia_v1_streaming": {
      "language_behaviour": "manual",
      "language": "string",
      "transcription_hint": "string",
      "endpointing": 0,
      "model_type": "fast",
      "audio_enhancer": true
    },
    "gladia_v2_streaming": {
      "model": "string",
      "endpointing": 0,
      "maximum_duration_without_endpointing": 0,
      "languages": [
        "string"
      ],
      "code_switching": true,
      "audio_enhancer": true,
      "speech_threshold": 0,
      "custom_vocabulary": true,
      "custom_vocabulary_config": {
        "default_intensity": 0,
        "vocabulary": [
          {
            "value": "string",
            "intensity": 0,
            "pronunciations": [
              "string"
            ],
            "language": "string"
          }
        ]
      },
      "sentiment_analysis": true,
      "region": "string"
    },
    "rev_streaming": {
      "language": "string",
      "metadata": "string",
      "custom_vocabulary_id": "string",
      "filter_profanity": true,
      "remove_disfluencies": true,
      "delete_after_seconds": 0,
      "detailed_partials": true,
      "start_ts": 0,
      "max_segment_duration_seconds": 0,
      "transcriber": "string",
      "enable_speaker_switch": true,
      "skip_postprocessing": true,
      "priority": "string"
    },
    "aws_transcribe_streaming": {
      "language_code": "string",
      "content_redaction_type": "string",
      "language_model_name": "string",
      "language_options": "string",
      "language_identification": true,
      "identify_multiple_languages": true,
      "partial_results_stability": "string",
      "pii_entity_types": "string",
      "preferred_language": "string",
      "show_speaker_label": true,
      "vocabulary_filter_method": "string",
      "vocabulary_filter_names": "string",
      "vocabulary_names": "string",
      "vocabulary_name": "string"
    },
    "speechmatics_streaming": {
      "language": "string",
      "additional_vocab": [
        {
          "content": "string",
          "sounds_like": [
            "string"
          ]
        }
      ],
      "diarization": "string",
      "speaker_diarization_config": {
        "max_speakers": 0
      },
      "enable_partials": true,
      "max_delay": 0,
      "max_delay_mode": "string",
      "output_locale": "string",
      "punctuation_overrides": {
        "permitted_marks": [
          "string"
        ],
        "sensitivity": 0
      },
      "operating_point": "string",
      "enable_entities": true
    },
    "meeting_captions": {}
  }
}
```
