## 데이터 단위

### 버퍼 (Buffer)

- **정의**: 오디오 데이터의 일정량을 임시 저장하는 역할입니다.
- **세부사항**: 1024개의 프레임이 하나의 버퍼를 구성합니다.

### 프레임 (Frame)

- **정의**: 오디오 샘플의 그룹입니다.
- **세부사항**: 각 버퍼는 1024개의 샘플로 이루어져 있습니다.

### 패킷 (Packet)

- **정의**: 네트워크를 통해 전송되는 데이터 묶음입니다.
- **세부사항**: 실시간 오디오 전송에서는 압축된 오디오 데이터가 패킷으로 분할되어 전송됩니다.

## 전체적인 데이터 흐름

1. **프레임 수집**:

   - 오디오 입력 장치는 오디오 샘플들을 프레임 단위로 수집합니다.

2. **버퍼 축적**:

   - 수집된 프레임들은 버퍼에 저장됩니다. 각 버퍼는 1024개의 프레임을 포함합니다.

3. **데이터 압축 및 패킷 생성**:

   - 버퍼에 저장된 데이터는 필요에 따라 압축되고, 패킷으로 분할되어 네트워크를 통해 전송됩니다.

4. **패킷 전송**:

   - 패킷들은 네트워크를 통해 송신자에서 수신자로 전송됩니다.
