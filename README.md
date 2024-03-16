# 시스템 거래
키움 API 프로젝트

from PyQt5. Qax 컨테이너 가져오기 *
from PyQt5. QtWidget 가져오기 *
from PyQt5. QtCore 가져오기 *

클래스 키움(QAXWidget):
    def __init__(자체):
        슈퍼 ().__init__()
        자신._make_kiwoom_instance()
        자신._set_signal_slots()
        자신._comm_connect ()
    def _make_kiwoom_instance(self): # 키움 클래스가 API를 사용할 수 있도록 등록하는 함수
        자신.Control("KHOPENAPI")을 설정합니다.KHOpenAPICtrl. 1")
    def _set_signal_slots(self): # API로 보내는 요청들을 받아 올 슬롯을 등록하는 함수
        자신.OnEventConnect.connect(자체)._login_slot) # 로그인 시도 결과에 대한 응답을 "_login_slot"으로 받도록 설정
    def _login_slot(자체, err_code): # 로그인 시도 결과에 대한 응답을 얻는 함수
        err_code == 0인 경우:
            인쇄 (" 연결") # 성공
        기타:
            인쇄 (" 연결되지 않음") # 실패

        self.login_event_loop.exit() # 로그인 시도 결과에 대한 응답 대기 종료
    def _comm_connect(self): # 로그인 요청 신호를 보낸 이후 응답 대기를 설정하는 함수: 로그인 함수
        self.dynamicCall("Commconnect()")"

        self.login_event_loop = QEventLoop() #로그인 시도 결과에 대한 응답 대기 시작
        self.login_event_loop.exec_()
