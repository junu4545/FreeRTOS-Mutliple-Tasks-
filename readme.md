# Project: FreeRTOS Multiple Tasks Control

## Introduction
This project demonstrates **Multi-tasking** in FreeRTOS by managing two concurrent tasks with identical priorities. I implemented `JUNTask1` (1s period) and `JUNTask2` (2s period) to explore **Preemptive Time-slicing** and **Context Switching**. By setting different delay intervals, I verified how the RTOS scheduler precisely manages CPU resources based on timing requirements.

## Environment
* **IDE**: Visual Studio 2022
* **OS**: FreeRTOS Windows Simulator

## Key Features
1. **Dual Task Management**: Successfully initialized and registered two independent tasks (`JUNTask1`, `JUNTask2`) with the same priority (Priority 1) using the `xTaskCreate()` API.
2. **Variable Periodic Execution**: Implemented distinct output intervals (1,000ms and 2,000ms) by combining `vTaskDelay()` with the `pdMS_TO_TICKS()` macro for each task.
3. **Safe Parameter Handling**: Prevented compiler warnings and ensured code stability by explicitly casting the unused `pvParameters` to `void` in both task functions.
4. **Minimalist System Configuration**: Maintained the execution environment in `mainCREATE_SIMPLE_BLINKY_DEMO_ONLY 1` mode to focus strictly on core scheduling and multitasking logic.

## Results
### **Logging**
In this project, **Logging** was utilized as a key tool to record and analyze scheduling behavior in a multi-tasking environment.
* **Interleaved Output Pattern**: Confirmed that `Task1` (1s) and `Task2` (2s) output to the terminal alternately. At the 2-second mark (even seconds), both tasks were logged simultaneously.
* **Execution Order Analysis**: When both tasks resume from the Blocked state at the same time (e.g., at 2s, 4s), `Task1` is typically logged above `Task2` due to its earlier registration order in the scheduler.
* **Operational Verification**: Through this logging process, I technically proved that FreeRTOS manages resources in real-time according to priorities and delay intervals.

---

## [한글 해석]

# 프로젝트: FreeRTOS 다중 태스크 제어

## 서론 (Introduction)
이 프로젝트는 동일한 우선순위를 가진 두 개의 동시 태스크를 관리함으로써 FreeRTOS의 **멀티태스킹**을 시연합니다. `JUNTask1`(1초 주기)과 `JUNTask2`(2초 주기)를 구현하여 **선점형 시분할(Preemptive Time-slicing)** 및 **문맥 교환(Context Switching)** 원리를 탐구하였습니다. 서로 다른 지연 간격을 설정함으로써 RTOS 스케줄러가 타이밍 요구 사항에 따라 CPU 자원을 얼마나 정밀하게 관리하는지 확인하였습니다.

## 환경 (Environment)
* **IDE**: Visual Studio 2022
* **OS**: FreeRTOS Windows Simulator

## 주요 특징 (Key Features)
1. **이중 태스크 관리**: `xTaskCreate()` API를 사용하여 동일한 우선순위(Priority 1)를 가진 두 개의 독립적인 태스크(`JUNTask1`, `JUNTask2`)를 성공적으로 초기화하고 등록하였습니다.
2. **가변 주기 실행**: 각 태스크에 대해 `vTaskDelay()`와 `pdMS_TO_TICKS()` 매크로를 결합하여 서로 다른 출력 간격(1,000ms 및 2,000ms)을 구현하였습니다.
3. **안전한 매개변수 처리**: 두 태스크 함수 모두에서 사용하지 않는 `pvParameters`를 `void`로 명시적 형변환하여 컴파일러 경고를 방지하고 코드 안정성을 확보하였습니다.
4. **최소한의 시스템 구성**: 핵심 스케줄링 및 멀티태스킹 로직에 집중하기 위해 실행 환경을 `mainCREATE_SIMPLE_BLINKY_DEMO_ONLY 1` 모드로 유지하였습니다.

## 결과 (Results)
### **로깅 (Logging)**
본 프로젝트에서 **로깅**은 멀티태스킹 환경에서의 스케줄링 동작을 기록하고 분석하는 핵심 도구로 활용되었습니다.
* **교차 출력 패턴**: 1초 주기의 `Task1`과 2초 주기의 `Task2`가 터미널에 교차로 출력
