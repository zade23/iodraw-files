```mermaid
classDiagram
    class VoiceInteractionDemo {
        -string _buffer
        +void Awake()
        +void OnVadChanged(bool vadStop)
        +void OnButtonPressed()
        +void OnNewSegment()
        +void OnProgressHandler()
        +void OnRecordStop()
        +void OnLanguageChanged(int index)
    }

    class WhisperManager {
        +event OnNewSegment
        +event OnProgress
        +string language
    }

    class MicrophoneRecord {
        +event OnRecordStop
        +bool vadStop
    }

    class Button {
        +void onClick.AddListener(Action listener)
    }

    class Dropdown {
        +int value
        +List<Option> options
        +void onValueChanged.AddListener(Action<int> listener)
    }

    class Toggle {
        +bool isOn
        +void onValueChanged.AddListener(Action<bool> listener)
    }

    VoiceInteractionDemo --> WhisperManager : 订阅 OnNewSegment
    VoiceInteractionDemo --> WhisperManager : 订阅 OnProgress
    VoiceInteractionDemo --> MicrophoneRecord : 订阅 OnRecordStop
    VoiceInteractionDemo --> Button : 订阅 onClick
    VoiceInteractionDemo --> Dropdown : 订阅 onValueChanged
    VoiceInteractionDemo --> Toggle : 订阅 onValueChanged
```