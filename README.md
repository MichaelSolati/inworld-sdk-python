# inworld-sdk

A Python SDK for interacting with [Inworld AI's platform](https://docs.inworld.ai/docs/intro).

## Description

This SDK provides a Python interface for working with Inworld AI's services, making it easy to integrate AI characters into your applications.

Currently, this SDK only supports the TTS API.

## Installation

You can install the package using pip:

```bash
pip install inworld-sdk
```

For development installation:

```bash
# Clone the repository
git clone https://github.com/MichaelSolati/inworld-sdk-python.git
cd inworld-sdk-python

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows, use: .\venv\Scripts\activate

# Install the package in development mode with all dependencies
pip install -e ".[dev]"
```

## Basic Usage

```python
import asyncio

import simpleaudio as sa

from inworld_sdk import InworldAIClient


async def main():
  # Initialize the client
  client = InworldAIClient(api_key="<YOUR_API_KEY>")

  # Example: Get voices
  voices = await client.tts.voices()
  print(voices)

  # Example: Synthesize and play speech
  text = "Hello! This is a test of the Inworld AI TTS system."
  sync_buffer = await client.tts.synthesizeSpeechAsWav(text)
  play_obj = sa.WaveObject.from_wave_file(sync_buffer)
  play_obj.play().wait_done()


if __name__ == "__main__":
  asyncio.run(main())
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
