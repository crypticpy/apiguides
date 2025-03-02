```json
{
  "api_guide": {
    "version": "1.1",
    "description": "Merged, concise OpenAI API guide for AI consumption. Combines best content from both sources, focusing on machine readability, consistent JSON structure, and advanced usage details.",

    "models": {
      "overview": "OpenAI offers diverse model families with varying capabilities, token limits, and pricing. Many support fine-tuning or advanced features like multimodal inputs (vision), audio generation, or complex reasoning tokens.",
      "categories": [
        {
          "name": "GPT Models",
          "description": "Flagship GPT series for text-based tasks, including optional multimodal (image) support and advanced planning. Fine-tuning supported on some variants.",
          "models": [
            {
              "id": "gpt-4.5-preview",
              "alias_for": "gpt-4.5-preview-2025-02-27",
              "capabilities": ["text", "image_input"],
              "max_input_tokens": 128000,
              "max_output_tokens": 16384,
              "description": "Largest GPT model, top-tier intelligence, agentic planning. Accepts text/image input."
            },
            {
              "id": "gpt-4o",
              "alias_for": "gpt-4o-2024-08-06",
              "capabilities": ["text", "image_input"],
              "max_input_tokens": 128000,
              "max_output_tokens": 16384,
              "description": "Versatile, high-intelligence GPT model. Accepts text/image. Good for creativity & conversation."
            },
            {
              "id": "gpt-4o-mini",
              "alias_for": "gpt-4o-mini-2024-07-18",
              "capabilities": ["text", "image_input"],
              "max_input_tokens": 128000,
              "max_output_tokens": 16384,
              "description": "Smaller, cheaper variant of GPT-4o. Good for fine-tuning or distillation from a larger GPT model."
            },
            {
              "id": "gpt-4-turbo",
              "alias_for": "gpt-4-turbo-2024-04-09",
              "capabilities": ["text"],
              "max_input_tokens": 128000,
              "max_output_tokens": 4096,
              "description": "Older GPT-4 version with fewer output tokens. Still suitable for high intelligence tasks."
            },
            {
              "id": "gpt-3.5-turbo",
              "alias_for": "gpt-3.5-turbo-0125",
              "capabilities": ["text"],
              "max_input_tokens": 16385,
              "max_output_tokens": 4096,
              "description": "Legacy GPT-3.5 chat model; overshadowed by gpt-4o-mini as of July 2024."
            }
          ]
        },
        {
          "name": "Reasoning Models",
          "description": "Reinforcement learning–trained for advanced reasoning, multi-step planning, and complex coding tasks. Produce hidden reasoning tokens.",
          "models": [
            {
              "id": "o1",
              "alias_for": "o1-2024-12-17",
              "capabilities": ["text", "image_input"],
              "max_input_tokens": 200000,
              "max_output_tokens": 100000,
              "description": "Flagship reasoning model for harder tasks. Slower but superior intelligence and domain generalization."
            },
            {
              "id": "o1-mini",
              "alias_for": "o1-mini-2024-09-12",
              "capabilities": ["text"],
              "max_input_tokens": 128000,
              "max_output_tokens": 65536,
              "description": "Faster, cheaper version of o1. Replaced by o3-mini for better intelligence at similar cost."
            },
            {
              "id": "o3-mini",
              "alias_for": "o3-mini-2025-01-31",
              "capabilities": ["text"],
              "max_input_tokens": 200000,
              "max_output_tokens": 100000,
              "description": "Latest small reasoning model. High intelligence, cost-effective for coding, math, multi-step logic."
            }
          ]
        },
        {
          "name": "Specialized Models",
          "description": "Models built for domain-specific tasks like real-time streaming, audio I/O, image generation, embeddings, and moderation.",
          "models": [
            {
              "id": "gpt-4o-realtime-preview",
              "alias_for": "gpt-4o-realtime-preview-2024-12-17",
              "capabilities": ["realtime_audio", "text"],
              "max_input_tokens": 128000,
              "max_output_tokens": 4096,
              "description": "Beta real-time text/audio responses via WebRTC/WebSocket."
            },
            {
              "id": "gpt-4o-audio-preview",
              "alias_for": "gpt-4o-audio-preview-2024-12-17",
              "capabilities": ["audio_io"],
              "max_input_tokens": 128000,
              "max_output_tokens": 16384,
              "description": "Beta model accepting audio input and producing audio output via REST."
            },
            {
              "id": "dall-e-3",
              "capabilities": ["image_generation"],
              "description": "Generates/edit images from text prompts. Latest generation of DALL·E."
            },
            {
              "id": "tts-1",
              "capabilities": ["text_to_speech"],
              "description": "Fast text-to-speech."
            },
            {
              "id": "tts-1-hd",
              "capabilities": ["text_to_speech"],
              "description": "High-quality text-to-speech."
            },
            {
              "id": "whisper-1",
              "capabilities": ["speech_to_text"],
              "description": "Speech recognition & translation, matches open-source Whisper with faster inference."
            },
            {
              "id": "text-embedding-3-large",
              "capabilities": ["text_embedding"],
              "output_dimension": 3072,
              "description": "Large embedding model, best for multi-lingual tasks."
            },
            {
              "id": "text-embedding-3-small",
              "capabilities": ["text_embedding"],
              "output_dimension": 1536,
              "description": "High-performance 3rd-gen embedding with smaller dimension."
            },
            {
              "id": "text-embedding-ada-002",
              "capabilities": ["text_embedding"],
              "output_dimension": 1536,
              "description": "2nd-gen embedding. Replaces older first-gen Ada embeddings."
            },
            {
              "id": "omni-moderation-latest",
              "alias_for": "omni-moderation-2024-09-26",
              "capabilities": ["moderation"],
              "max_tokens": 32768,
              "description": "Multi-modal moderation, analyzing both text and images."
            },
            {
              "id": "text-moderation-latest",
              "alias_for": "text-moderation-007",
              "capabilities": ["moderation"],
              "max_tokens": 32768,
              "description": "Latest text-only moderation model."
            }
          ]
        }
      ],
      "model_aliases": {
        "description": "Aliases are stable references like 'gpt-4o' or 'o3-mini' that periodically update to new dated snapshots. For production stability, consider referencing exact dated snapshots (e.g., 'gpt-4o-2024-08-06').",
        "example_request": {
          "language": "python",
          "code": "from openai import OpenAI\nclient = OpenAI()\n\ncompletion = client.chat.completions.create(\n    model=\"gpt-4o\",\n    messages=[\n        {\"role\": \"developer\", \"content\": \"You are a helpful assistant.\"},\n        {\"role\": \"user\", \"content\": \"Write a haiku about recursion.\"}\n    ]\n)\n\nprint(completion.choices[0].message)"
        },
        "example_response": {
          "model": "gpt-4o-2024-08-06",
          "message": {
            "role": "assistant",
            "content": "Code within a loop,\nFunction calls itself again,\nInfinite echoes."
          }
        }
      }
    },

    "endpoints": {
      "chat_completions": {
        "path": "/v1/chat/completions",
        "description": "Generates text-based responses (or calls functions). Supports structured outputs, streaming, image/audio inputs, reasoning tokens, etc.",
        "supported_models": [
          "All o-series",
          "GPT-4.5",
          "GPT-4o (except Realtime preview)",
          "GPT-4o-mini",
          "GPT-4",
          "GPT-3.5 Turbo",
          "chatgpt-4o-latest",
          "Fine-tuned versions of gpt-4o, gpt-4o-mini, gpt-4, gpt-3.5-turbo"
        ],
        "request_parameters": [
          {
            "name": "model",
            "type": "string",
            "required": true,
            "description": "Model ID or alias, e.g. 'gpt-4o', 'o3-mini'."
          },
          {
            "name": "messages",
            "type": "array",
            "required": true,
            "description": "Array of messages. Roles: 'user', 'developer', 'assistant'. Provide conversation context."
          },
          {
            "name": "tools",
            "type": "array",
            "required": false,
            "description": "Definitions for function calling. Each tool is a function with name/parameters."
          },
          {
            "name": "response_format",
            "type": "object",
            "required": false,
            "description": "Enforce structured outputs. E.g. {\"type\": \"json_schema\", \"json_schema\": {...}, \"strict\": true}."
          },
          {
            "name": "reasoning_effort",
            "type": "string",
            "required": false,
            "description": "For o-series models: 'low', 'medium', or 'high' controlling how many reasoning tokens are used."
          },
          {
            "name": "max_completion_tokens",
            "type": "integer",
            "required": false,
            "description": "Cap on total tokens (reasoning + visible output). Avoid partial outputs if too low."
          },
          {
            "name": "store",
            "type": "boolean",
            "required": false,
            "description": "If true, store completions up to 30 days. Avoid storing sensitive data."
          }
        ],
        "response_fields": [
          { "name": "id", "type": "string" },
          { "name": "object", "type": "string" },
          { "name": "created", "type": "integer" },
          { "name": "model", "type": "string" },
          { "name": "choices", "type": "array" },
          { "name": "usage", "type": "object" }
        ],
        "notes": [
          "Image inputs with gpt-4.5-preview, gpt-4o, o1, gpt-4o-mini, etc. are not eligible for zero retention.",
          "Audio outputs stored for 1 hour, not eligible for zero retention.",
          "Schemas for structured outputs or function definitions are not eligible for zero retention."
        ]
      },
      "embeddings": {
        "path": "/v1/embeddings",
        "description": "Generates numeric vector embeddings from text. Useful for search, semantic similarity, classification.",
        "supported_models": [
          "text-embedding-3-small",
          "text-embedding-3-large",
          "text-embedding-ada-002"
        ]
      },
      "audio_transcriptions": {
        "path": "/v1/audio/transcriptions",
        "description": "Convert speech audio to text (STT).",
        "supported_models": ["whisper-1"]
      },
      "audio_translations": {
        "path": "/v1/audio/translations",
        "description": "Translate speech audio to English.",
        "supported_models": ["whisper-1"]
      },
      "audio_speech": {
        "path": "/v1/audio/speech",
        "description": "Text-to-speech. Converts input text to spoken audio (mp3, opus, etc.).",
        "supported_models": ["tts-1", "tts-1-hd"],
        "request_parameters": [
          {
            "name": "model",
            "type": "string",
            "required": true,
            "description": "Use 'tts-1' or 'tts-1-hd'."
          },
          {
            "name": "input",
            "type": "string",
            "required": true,
            "description": "Text to synthesize into speech."
          },
          {
            "name": "voice",
            "type": "string",
            "required": true,
            "description": "Desired voice, e.g. 'alloy', 'echo', 'fable', 'onyx', etc."
          },
          {
            "name": "response_format",
            "type": "string",
            "required": false,
            "description": "Audio format: 'mp3', 'opus', 'aac', 'wav', 'flac', or 'pcm'. Default 'mp3'."
          }
        ]
      },
      "images_generations": {
        "path": "/v1/images/generations",
        "description": "Generates images from text prompts. Also includes /edits and /variations sub-endpoints.",
        "supported_models": ["dall-e-2", "dall-e-3"]
      },
      "moderations": {
        "path": "/v1/moderations",
        "description": "Classify text/image content for policy compliance. Nudity, violence, self-harm, etc.",
        "supported_models": [
          "text-moderation-stable",
          "text-moderation-latest",
          "omni-moderation-latest"
        ]
      },
      "realtime": {
        "path": "/v1/realtime",
        "description": "Realtime streaming for GPT-4o-realtime-preview. Beta for continuous text/audio interactions.",
        "supported_models": [
          "gpt-4o-realtime-preview",
          "gpt-4o-realtime-preview-2024-10-01"
        ],
        "notes": "Uses WebRTC/WebSocket for streaming. Limited availability."
      }
    },

    "guides": {
      "text_generation": {
        "description": "How to generate text from a prompt using /v1/chat/completions.",
        "prompt_engineering": {
          "description": "Focus on providing clear instructions and context. For GPT models, use role-based messages (user, developer, assistant). Provide relevant knowledge or example dialogs for better results.",
          "retrieval_augmented_generation": "You can provide external context or data to the model. This is known as RAG. Consider storing domain data externally and injecting relevant info at runtime."
        },
        "multi_turn_conversations": "Include all previous messages to maintain context. Large conversation can reach token limits—prune or summarize older turns if needed.",
        "context_window_management": "Input tokens + output tokens + (optionally) reasoning tokens must be under the model's context limit. Use token-counting tools like tiktoken to estimate usage.",
        "optimization": [
          {
            "goal": "Accuracy",
            "techniques": ["Add relevant context (RAG)", "Better prompts", "Model fine-tuning"]
          },
          {
            "goal": "Cost",
            "techniques": ["Use fewer tokens (short prompts)", "Use smaller models if possible"]
          },
          {
            "goal": "Latency",
            "techniques": ["Smaller models", "Parallel requests", "Prompt refinement"]
          }
        ]
      },
      "vision": {
        "description": "Models like gpt-4o, gpt-4.5-preview, o1 can interpret image inputs. Provide URLs or base64 data. 'detail' parameter controls resolution. Low detail is cheaper but less accurate.",
        "multiple_image_inputs": "You can pass arrays of images for multi-image queries. The model processes each image in context.",
        "fidelity_control": {
          "parameter": "detail",
          "options": ["low", "high", "auto"],
          "low_res_cost": "85 tokens total",
          "high_res_cost": "85 + (170 tokens * number_of_512px_tiles)",
          "size_guidelines": {
            "low_res": "512x512",
            "high_res": "Up to 768x2000, then scaled into 512px tiles"
          }
        },
        "limitations": [
          "Not suitable for specialized medical images or robust spatial tasks (like detailed object location).",
          "Struggles with small text or unusual rotations.",
          "May give approximate counts or partial info in complex images."
        ]
      },
      "audio_generation": {
        "description": "Use GPT-4o-audio-preview or the dedicated TTS endpoints. You can generate speech from text or respond to audio inputs. Also supports multi-turn audio conversations by referencing audio IDs in subsequent messages.",
        "input_output_combinations": [
          "Text in → text + audio out",
          "Audio in → text + audio out",
          "Audio in → text out",
          "Text + audio in → text + audio out",
          "Text + audio in → text out"
        ],
        "token_approximation": "~1 hour of audio input is ~128k tokens in GPT-4o-audio."
      },
      "text_to_speech": {
        "description": "Endpoints: /v1/audio/speech with tts-1 or tts-1-hd. Provide text input and voice. Returns an audio file (mp3, opus, etc.).",
        "voices": ["alloy", "ash", "coral", "echo", "fable", "onyx", "nova", "sage", "shimmer"],
        "supported_languages": [
          "Afrikaans", "Arabic", "Armenian", "Azerbaijani", "Belarusian", "Bosnian", "Bulgarian",
          "Catalan", "Chinese", "Croatian", "Czech", "Danish", "Dutch", "English", "Estonian",
          "Finnish", "French", "Galician", "German", "Greek", "Hebrew", "Hindi", "Hungarian",
          "Icelandic", "Indonesian", "Italian", "Japanese", "Kannada", "Kazakh", "Korean",
          "Latvian", "Lithuanian", "Macedonian", "Malay", "Marathi", "Maori", "Nepali", "Norwegian",
          "Persian", "Polish", "Portuguese", "Romanian", "Russian", "Serbian", "Slovak",
          "Slovenian", "Spanish", "Swahili", "Swedish", "Tagalog", "Tamil", "Thai", "Turkish",
          "Ukrainian", "Urdu", "Vietnamese", "Welsh"
        ],
        "streaming": "Use chunked transfer or streaming clients for real-time audio playback."
      },
      "speech_to_text": {
        "description": "Use whisper-1. Submit audio via /v1/audio/transcriptions or /v1/audio/translations for English translation. Returns recognized text."
      },
      "reasoning_models": {
        "description": "o-series excels at multi-step reasoning, complex logic, and coding solutions. They generate hidden reasoning tokens that count against your usage.",
        "reasoning_effort": "Set 'reasoning_effort' to low, medium, or high. Default is medium. High yields deeper analysis but slower, more expensive.",
        "max_completion_tokens": "Caps total tokens for reasoning + final output. If reached, partial or truncated output can occur."
      },
      "structured_outputs": {
        "description": "Enforces JSON schema compliance in model responses. Helps ensure correct field types, keys, and value domains.",
        "benefits": ["Guaranteed JSON structure", "Schema validation", "Clear refusals if not feasible"],
        "usage": "Set response_format to { \"type\": \"json_schema\", \"json_schema\": { ... }, \"strict\": true }. Model always returns valid JSON or refusal field.",
        "supported_schemas": [
          "String", "Number", "Boolean", "Integer", "Object", "Array", "Enum", "anyOf (nested conditions)"
        ],
        "limitations": [
          "Root object must not be anyOf",
          "All fields must be required or typed with null for optional",
          "Max nesting depth = 5",
          "Max total schema string length = 15k",
          "No patternProperties, minItems, maxItems, or advanced JSON schema keywords"
        ],
        "refusals": "If content is disallowed or query is not feasible, model returns a 'refusal' field instead of valid JSON."
      },
      "function_calling": {
        "description": "Augment model with external code or data. Provide 'tools' array with function definitions. The model may call zero, one, or multiple functions, returning JSON with function name/arguments. You execute and return results.",
        "use_cases": ["Data lookups (RAG)", "API calls", "Database writes", "Custom business logic", "Agentic workflows"],
        "function_definition": {
          "fields": ["name", "description", "parameters (JSON schema)"],
          "strict_mode": "Set 'strict': true to ensure calls match schema exactly (requires additionalProperties=false, all fields required)."
        },
        "tool_choice": "Controls model's usage of tools. auto|none|required|{type:'function',function:{name:'...'}}",
        "parallel_function_calling": "If true, model may call multiple functions in a single turn. If false, it calls at most one per turn.",
        "handling_function_calls": "Parse the returned function calls, run your code, pass results back to the model as a 'tool' message. Then the model can finalize its user-facing output.",
        "formatting_results": "Return strings in the tool message. Could be JSON, plain text, or any format. The model can incorporate that result in further steps.",
        "streaming": "You can stream partial function calls and parse arguments as they arrive."
      }
    },

    "data_usage": {
      "policy": "Data is not used for model training unless explicitly opted in. Default retention of logs is 30 days for abuse detection.",
      "zero_retention": "For sensitive apps, zero data retention can be requested. Some inputs are not eligible (image, audio outputs, etc.).",
      "exceptions": [
        "When structured_outputs or function definitions are used, the schema itself is not zero-retention eligible.",
        "Image inputs for certain models are also excluded from zero retention.",
        "Audio outputs are stored for 1 hour for multi-turn audio usage."
      ]
    },

    "token_and_cost_guide": {
      "token_usage": {
        "reasoning_models": "o-series produce hidden reasoning tokens, billed as output. Provide enough 'max_completion_tokens' to avoid truncation.",
        "vision_inputs": "detail=low costs 85 tokens. detail=high uses additional tokens per 512px tile (170 each + 85 base).",
        "audio_inputs": "~1 hour = 128k tokens for gpt-4o-audio or related audio-capable models."
      },
      "billing_reference": "https://openai.com/api/pricing"
    },

    "fine_tuning": {
      "description": "Refine model behavior on domain-specific data. Available on GPT-3.5, GPT-4, GPT-4o, GPT-4o-mini, and some vision models.",
      "method": "Upload training data via /v1/files, create fine_tuning/jobs, then reference the resulting model ID for future requests. Evaluate carefully to confirm improved performance.",
      "recommendations": "Keep data consistent in style. Minimally 1000 examples recommended. Evaluate partial epochs to avoid overfitting."
    },

    "moderation": {
      "description": "Check text or images for disallowed or sensitive content via moderation models. Supports categories like hate, violence, self-harm, sexual content.",
      "models": ["omni-moderation-* (multimodal)", "text-moderation-* (text-only)"],
      "policy_reference": "https://openai.com/policies/usage-policies"
    }
  }
}
```
