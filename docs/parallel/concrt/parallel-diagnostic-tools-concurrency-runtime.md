---
description: '詳細情報: Parallel 診断ツール (同時実行ランタイム)'
title: 並列診断ツール (コンカレンシー ランタイム)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: ac6afbbc2bfef3793e9685a7c9e1054b7d677bd8
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951523"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>並列診断ツール (コンカレンシー ランタイム)

Visual Studio は、マルチ スレッド アプリケーションのデバッグおよびプロファイリングを広範にサポートします。

## <a name="debugging"></a>デバッグ

Visual Studio デバッガーには、[並列 **スタック** ] ウィンドウ、[ **並列タスク** ] ウィンドウ、および [ **並列ウォッチ** ] ウィンドウがあります。 詳細については、「 [チュートリアル: 並列アプリケーションのデバッグ](/visualstudio/debugger/walkthrough-debugging-a-parallel-application) 」および「 [方法: 並列ウォッチウィンドウを使用する](/visualstudio/debugger/how-to-use-the-parallel-watch-window)」を参照してください。

## <a name="profiling"></a>プロファイル

プロファイリングツールには、マルチスレッドアプリケーションとその他のプログラムとの対話方法に関する、グラフィカルで表形式の数値情報を表示する3つのデータビューが用意されています。 ビューを使用すると、関心のある領域をすばやく特定したり、グラフィカルな表示のポイントから呼び出し履歴、呼び出しサイト、およびソースコードに移動したりすることができます。 詳細については、「[コンカレンシー ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)」を参照してください。

## <a name="event-tracing"></a>イベント トレーシング

同時実行ランタイムは [Windows イベントトレーシング](/windows/win32/ETW/event-tracing-portal) (ETW) を使用して、さまざまなイベントが発生したときにプロファイラーなどのインストルメンテーションツールに通知します。 これらのイベントには、スケジューラがアクティブ化または非アクティブ化されたとき、コンテキストの開始、終了、ブロック、ブロック解除、または生成が発生したとき、および並列アルゴリズムが開始または終了するタイミングが含まれます。

[同時実行ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)などのツールは、この機能を使用します。そのため、通常、これらのイベントを直接操作する必要はありません。 ただし、これらのイベントは、カスタムプロファイラーを開発している場合や、 [Windows パフォーマンスツールキット](/windows-hardware/test/wpt/)などのイベントトレースツールを使用する場合に役立ちます。

同時実行ランタイムは、トレースが有効になっている場合にのみ、これらのイベントを発生させます。 [Concurrency:: EnableTracing](reference/concurrency-namespace-functions.md#enabletracing)関数を呼び出してイベントのトレースを有効にし、 [Concurrency::D isabletracing](reference/concurrency-namespace-functions.md#disabletracing)関数を呼び出してトレースを無効にします。

次の表では、イベントトレースが有効な場合にランタイムによって発生するイベントについて説明します。

|Event|説明|[値]|
|-----------|-----------------|-----------|
|[concurrency:: ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|同時実行ランタイムの ETW プロバイダー識別子。|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency:: ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|コンテキストに関連するイベントをマークします。|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrency::P PLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|[Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズムの呼び出しへの開始と終了をマークします。|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrency::P PLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|[Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)アルゴリズムの呼び出しへの開始と終了をマークします。|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrency::P PLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|[Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)アルゴリズムの呼び出しへの開始と終了をマークします。|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency:: スケジューラ Eventguid](reference/concurrency-namespace-constants1.md#schedulereventguid)|[タスクスケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)に関連するイベントをマークします。|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency:: VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|仮想プロセッサに関連するイベントをマークします。|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

同時実行ランタイムは、次のイベントを定義しますが、現在はを発生させません。 ランタイムは、今後使用するためにこれらのイベントを予約します。

- [concurrency:: ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency:: ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency:: ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency:: LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency:: ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

[Concurrency:: ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype)列挙体は、イベントが追跡する可能性のある操作を指定します。 たとえば、アルゴリズムの開始時に、 `parallel_for` ランタイムはイベントを発生させ、を `PPLParallelForEventGuid` `CONCRT_EVENT_START` 操作として提供します。 アルゴリズムが `parallel_for` 戻る前に、ランタイムは再びイベントを発生させ、を `PPLParallelForEventGuid` `CONCRT_EVENT_END` 操作として提供します。

次の例は、の呼び出しのトレースを有効にする方法を示してい `parallel_for` ます。 ランタイムは、の最初の呼び出しをトレースしません `parallel_for` 。これは、トレースが有効になっていないためです。 を呼び出すと、 `EnableTracing` ランタイムはの2回目の呼び出しをトレースでき `parallel_for` ます。

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

ランタイムは、とを呼び出す回数を追跡し `EnableTracing` `DisableTracing` ます。 したがって、を複数回呼び出す場合は、 `EnableTracing` `DisableTracing` トレースを無効にするために同じ回数を呼び出す必要があります。

## <a name="see-also"></a>関連項目

[コンカレンシー ランタイム](../../parallel/concrt/concurrency-runtime.md)
