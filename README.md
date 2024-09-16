# APIHook
타겟 프로세스에 DLL Injection을 수행한 후 Trampoline hook 기법을 사용해서 타겟 프로세스의 제어 흐름을 변경하는 프로그램입니다.
Test용으로 제작한 터미널 기반 채팅 서버 프로그램(타겟 프로그램)의 PID값과 Injection용 DLL이 위치한 경로를 인수로 첨부해서 프로그램을 실행하면 타겟 프로세스의 핸들값을 가져와서 프로세스 내부에 DLL을 추가할 메모리 영역을 확보하고 Thread 생성을 통해 Injection용 DLL을 실행시킵니다. Injection에 성공한 DLL의 내부에서는 send 함수를 호출할때 제가 임의로 만든 MySend로 진입하도록 제어 흐름을 변경하였고, MySend 함수 내부에서 임의의 코드를 거친 후 리턴하기 전에 본래의 send 함수를 호출합니다. Windows API를 사용하므로 Windows OS에서만 동작합니다.
