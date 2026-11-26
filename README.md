# Misty Robot Receptionist

A Python-based smart-receptionist prototype for Misty. It brings together a QR-code check-in flow, a visitor log, Misty's camera and voice interface, and a locally loaded GPT4All language model.

## Features and implementation

- Connects to a Misty robot through the Misty Python SDK.
- Captures QR-code images with Misty's camera (640 × 480) and scans them with OpenCV's `QRCodeDetector`.
- Tracks visitor details and visit counts in `output/visitor_info.json`.
- Uses GPT4All with the `Llama-3.2-1B-Instruct-Q4_0.gguf` model for question answering.
- Supports Misty-connected, text-only, and fallback paths in the program.
- Uses Misty's speech/audio features and SpeechRecognition for speech transcription; the transcription path uses Google's recognition service and therefore requires network access.

The main entry point is `programs/__main__.py`. `additional_files/` contains earlier receptionist iterations, a QR generator, and experiments; QR test images are in `qr_codes/`. A project document is also provided as `Documentation.docx`.

## Requirements and running

The entry-point documentation lists these Python dependencies: `misty-sdk`, `websocket-client`, `opencv-python-headless`, `gpt4all`, `typer`, `image`, `pyaudio`, `speechrecognition`, and `pyttsx3`. Audio and model-runtime support may also require operating-system packages; see the entry-point notes and GPT4All documentation for platform-specific setup.

From the repository root, run the program as a module:

```bash
python -m programs
```

The program asks whether to use its text-only interface. The connected-robot path requires a reachable Misty and compatible camera/audio setup. GPT4All may need to download the selected model the first time it is used. Review and configure the robot connection settings in the entry point before running it in your environment.

## Scope and limitations

This is a prototype, not a hardened reception or visitor-management product. It depends on compatible robot hardware, working camera and audio, a local model runtime, and network access for speech transcription. Visitor records are stored locally as JSON; treat that file as personal data and protect or remove it appropriately.

## Related links

- [Portfolio project details](https://kasurancodes.github.io/misty.html)
- [Max McGill's portfolio](https://kasurancodes.github.io/)
