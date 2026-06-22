# Lab 8 - LLM Reasoning & Context-aware Decision for AIoT

Du an Lab 8 minh hoa cach dung LLM de tong hop ngu canh, giai thich tinh huong va dua ra khuyen nghi an toan cho he thong AIoT. Ung dung so sanh ba muc ra quyet dinh: chi cam bien, cam bien ket hop cac model AI, va cam bien + AI models + LLM reasoning.

## Thanh phan chinh

- `app.py`: FastAPI backend, dashboard, API reasoning, live telemetry va safety gate.
- `index.html`: giao dien web de quan sat scenario va ket qua so sanh.
- `run_lab8_demo.py`: script chay demo va kiem tra nhanh cac endpoint quan trong.
- `data/`: prompt templates va du lieu scenario.
- `docs/`: tai lieu huong dan chi tiet cho bai lab.
- `models/`: thu muc mo phong noi luu model/pretrained assets.
- `outputs/`: log telemetry, context packet, latency, comparison va audit.

## Cai dat

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

Neu dung macOS/Linux:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Chay ung dung

```bash
uvicorn app:app --reload --host 0.0.0.0 --port 8000
```

Mo trinh duyet tai:

```text
http://127.0.0.1:8000/
```

## Chay demo nhanh

```bash
python run_lab8_demo.py
```

Script demo se goi cac endpoint mau nhu health check, danh sach scenario, compare three levels va vision reasoning o che do mock.

## Che do LLM

- `mock`: chay offline, khong can API key, Internet hoac local model.
- `local`: goi Ollama tai `http://localhost:11434`.
- `api`: placeholder/fallback de co the gan cloud API khi can.

Vi du goi endpoint:

```text
GET /compare-three-levels/lab_overcrowded_high_co2?mode=mock
GET /reason/fire_alarm_conflict?mode=mock
POST /vision-reason/fire_alarm_conflict?mode=mock
```

## Scenario mau

- Lop hoc thong minh co CO2 tang nhanh va phong dong nguoi.
- Canh bao chay bi mau thuan voi bang chung cam bien.
- Nghi ngo te nga voi confidence chua du cao.
- Khu vuc cong truong co nguoi khong du bao ho.
- Giam sat cay trong voi dau hieu benh va do am cao.

## Ghi chu an toan

LLM trong bai lab chi dong vai tro ho tro ra quyet dinh. Safety gate trong backend chan dieu khien truc tiep actuator va yeu cau human review voi cac tinh huong rui ro cao hoac bang chung mau thuan.
