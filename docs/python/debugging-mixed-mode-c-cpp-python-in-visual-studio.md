---
title: Python 混和模式偵錯
description: 在 Visual Studio 中同時對 C++ 和 Python 進行偵錯，包括在環境之間逐步執行、檢視值和評估運算式。
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 85118cebfa862a1575762985d41df61ef76b5cc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949320"
---
# <a name="debug-python-and-c-together"></a>同時對 Python 和 C++ 進行偵錯

多數的標準 Python 偵錯工具都僅支援對 Python 程式碼進行偵錯。 不過，實際上在需要高效能或是能直接叫用平台 API 的情況下，會將 Python 搭配 C 或 C++ 使用。 (如需逐步解說，請參閱[建立適用於 Python 的 C++ 延伸模組](working-with-c-cpp-python-in-visual-studio.md))。

Visual Studio 有針對 Python 及原生 C/C++ 提供整合式的同時混合模式偵錯，前提是您必須在 Visual Studio 安裝程式中針對 [Python 開發] 工作負載選取 [Python 原生開發工具] 選項。

> [!Note]
> Visual Studio 2015 和更早版本中適用於 Visual Studio 1.x 的 Python 工具不支援混合模式偵錯。

混合模式偵錯包括下列於本文所述的功能：

- 合併的呼叫堆疊
- 在 Python 和機器碼之間逐步執行
- 這兩種類型程式碼中的中斷點
- 請參閱原生框架中 Python 的物件表示法 (反之亦然)
- 在 Python 專案或 C++ 專案的內容中進行偵錯

![Visual Studio 中的 Python 混合模式偵錯](media/mixed-mode-debugging.png)

![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") 如需使用 Visual Studio 建立、測試和偵測原生 C 模組的簡介，請參閱 [深入探討：建立原生模組](https://youtu.be/D9RlT06a1EI) (youtube.com、9m 分09秒) 。 本影片適用於 Visual Studio 2015 和 Visual Studio 2017。


## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>在 Python 專案中啟用混合模式偵錯

1. 以滑鼠右鍵按一下 **方案總管** 的 Python 專案，選取 [ **屬性**]，選取 [ **調試** 程式] 索引標籤，然後選取 [ **啟用原生程式碼調試** 程式]。 這個選項會啟用所有偵錯工作階段的混合模式。

    ![啟用原生程式碼偵錯](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > 當您啟用機器碼的偵錯工具時，Python 輸出視窗可能會在程式完成時立即消失，而不會讓您正常 **按下任何鍵以繼續** 暫停。 若要強制暫停，請在 `-i` 啟用機器碼偵錯工具時，將選項新增至 [偵錯工具] 索引標籤上的 [**執行**  >  **解譯器引數**] 欄位。  此引數會在程式碼完成之後，將 Python 解譯器放入互動模式中，此時它會等候您按下 **Ctrl** + **Z**  >  **enter** 結束。

1. 將混合模式偵錯工具附加至現有的進程 (**Debug**  >  **附加至進程**) 時，請使用 [**選取**] 按鈕來開啟 [**選取程式碼類型**] 對話方塊。 然後設定 [偵錯這些程式碼類型] 選項，並同時選取清單中的 [原生] 和 [Python]：

    ![選取原生和 Python 程式碼類型](media/mixed-mode-debugging-code-type.png)

    程式碼類型設定為持續性，因此，如果您稍後附加至其他進程時想停用混合模式的偵錯工具，請清除 **Python** 程式碼類型。

    除了選取 (或不選取) [原生] 以外，您還可以選取其他程式碼類型。 例如，如果受控應用程式裝載 CPython （接著使用原生延伸模組），而您想要將這三個模組全部進行偵錯工具，您可以同時檢查 **Python**、 **原生** 和 **managed** 以進行統一的偵錯工具，包括合併的呼叫堆疊和三個執行時間之間的逐步執行。

1. 當您首次在混合模式開始偵錯時，可能會看到 [需要 Python 符號] 對話方塊 (請參閱[混合模式偵錯的符號](debugging-symbols-for-mixed-mode-c-cpp-python.md))。 針對任何指定的 Python 環境，符號只需安裝一次。 如果您透過 Visual Studio 安裝程式 (Visual Studio 2017 和更新版本) 安裝 Python 支援，就會自動包含符號。

1. 若要在偵錯工具時提供標準 Python 的原始程式碼，請造訪 [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/) ，下載適用于您版本的封存，並將它解壓縮至資料夾。 每當提示您時，請將 Visual Studio 指向該資料夾中的特定檔案。

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>在 C/C++ 專案中啟用混合模式偵錯

Visual Studio (2017 15.5 版和更新版本) 支援從 C/C++ 專案進行混合模式偵錯 (例如，[以 python.org 所述方式將 Python 內嵌至另一個應用程式](https://docs.python.org/3/extending/embedding.html)時)。 若要啟用混合模式偵錯，請設定 C/C++ 專案以啟動 [Python/原生偵錯工具]：

1. 以滑鼠右鍵按一下 [方案總管] 中的 C/C++ 專案，然後選取 [屬性]。
1. 選取 [偵錯] 索引標籤，從 [要啟動的偵錯工具] 中選取 [Python/原生偵錯工具]，然後選取 [確定]。

    ![在 C/C++ 專案中選取 [Python/原生偵錯工具]](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> 如果您沒有選取 **python/原生調試** 程式的選項，您必須先使用 VS 安裝程式安裝 **python 原生開發工具** 。 您可以在 Python 開發工作負載下找到它作為選項。 如需詳細資訊，請參閱 [如何在 Windows 上的 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)。

使用此方法時，請留意到您並無法對 *py.exe* 啟動器本身進行偵錯，因為它會繁衍出偵錯工具無法附加至的子 *python.exe* 處理序。 如果您想要搭配引數直接啟動 *python.exe*，請變更 [Python/原生偵錯工具] 屬性中的 [命令] 選項 (如上圖所示) 以指定 *python.exe* 的完整路徑，然後在 [命令引數] 中指定引數。

### <a name="attaching-the-mixed-mode-debugger"></a>附加混合模式偵錯工具

針對所有舊版的 Visual Studio，只能在於 Visual Studio 中啟動 Python 專案時啟用直接混合模式偵錯，因為 C/C++ 專案只能使用原生偵錯工具。 不過，您可以分別附加偵錯工具：

1. 啟動 c + + 專案而不進行調試 (不需進行調試的 **Debug**  >  **啟動**，或按 **Ctrl** + **F5**) 。
1. 選取 [ **Debug**  >  **附加至進程**]。 在出現的對話方塊中，選取適當的進程，然後使用 [ **選取** ] 按鈕來開啟 [ **選取程式碼類型** ] 對話方塊，您可以在其中選取 [ **Python**]：

    ![附加偵錯工具時，選取 Python 作為偵錯類型](media/mixed-mode-debugging-attach-type.png)

1. 選取 [確定] 關閉該對話方塊，然後選取 [附加] 啟動偵錯工具。
1. 您可能需要在 C++ 應用程式中加入適合的暫停或延遲，以確保它不會立即呼叫您要偵錯的 Python 程式碼，讓您有機會可以附加偵錯工具。

## <a name="mixed-mode-specific-features"></a>混和模式的特定功能

- [合併的呼叫堆疊](#combined-call-stack)
- [在 Python 和機器碼之間逐步執行](#step-between-python-and-native-code)
- [原生程式碼中的 PyObject 值檢視](#pyobject-values-view-in-native-code)
- [Python 程式碼中的原生值檢視](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>合併的呼叫堆疊

[ **呼叫堆疊** ] 視窗會顯示兩個交錯的原生和 Python 堆疊框架，並在兩者之間標示轉換：

![合併的呼叫堆疊與混合模式偵錯](media/mixed-mode-debugging-call-stack.png)

如果設定 [工具] > [選項] > [偵錯] > [一般] > [啟用 Just My Code] 選項，轉換會顯示為 [外部程式碼]，而不指定轉換的方向。

按兩下任一呼叫框架會讓它成為使用中，可能的話，會開啟適當的原始程式碼。 如果沒有原始程式碼，框架仍會是使用中，並可檢查區域變數。

### <a name="step-between-python-and-native-code"></a>在 Python 和機器碼之間逐步執行

當您使用 [**逐步** 執行] (**F11**) 或 **跳出** (**Shift** + **F11**) 命令時，混合模式偵錯工具可正確處理常式代碼類型之間的變更。 例如，當 Python 呼叫某個在 C 中實作之類型的方法時，在該方法的呼叫中逐步執行時，會停在實作該方法的原生函式開頭。 同樣地，當原生程式碼呼叫一些 Python API 函式時，會叫用 Python 程式碼。 例如，在原先定義於 Python 中的某個函式值上逐步執行到 `PyObject_CallObject`，會停在 Python 函式的開頭。 對於透過 [ctypes](https://docs.python.org/3/library/ctypes.html) 從 Python 叫用的原生函式，也支援從 Python 逐步執行到原生函式。

### <a name="pyobject-values-view-in-native-code"></a>原生程式碼中的 PyObject 值檢視

當原生 (C 或 c + +) 框架為使用中時，其區域變數會顯示在偵錯工具的 [ **區域變數** ] 視窗中。 在原生 Python 延伸模組中，其中有許多變數都是 `PyObject` 類型 (即 `_object` 的 typedef)，或是一些其他基本 Python 類型 (請參閱下方清單)。 在混合模式的偵錯工具中，這些值會顯示標示為 **[Python view]** 的其他子節點。 展開時，此節點會顯示變數的 Python 表示法，您所看到的一切，會與參考相同物件的本機變數出現在 Python 框架時相同。 此節點的子系是可編輯的。

![[區域變數] 視窗中的 [Python 檢視]](media/mixed-mode-debugging-python-view.png)

若要停用這項功能，請以滑鼠右鍵按一下 [區域變數] 視窗的任意處，然後切換 [Python] > [顯示 Python 檢視節點] 功能表選項：

![在 [區域變數] 視窗中啟用 [Python 檢視]](media/mixed-mode-debugging-enable-python-view.png)

如果啟用) ，會顯示 **[Python view]** 節點 (的 C 類型：

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

**[Python view]** 不會自動針對您自行撰寫的類型顯示。 撰寫 Python 3.x 的延伸模組時，這通常不會造成問題，因為所有物件最終都會有 `ob_base` 上述其中一個類型的欄位，因而導致 **[Python view]** 出現。

不過，針對 Python 2.x，每個物件類型通常會將其標頭宣告為內嵌欄位的集合，而且自訂的撰寫類型和 C/C++ 程式碼中類型系統層級的 `PyObject` 之間沒有關聯。 若要啟用這種自訂類型的 [Python 檢視] 節點，請編輯 [Python 工具安裝目錄](installing-python-support-in-visual-studio.md#install-locations)中的 *PythonDkm.natvis* 檔案，然後直接在 C 結構或 C++ 類別的 XML 中新增另一個元素。

有一個替代 (也是更好) 的選項是依循 [PEP 3123 (英文)](https://www.python.org/dev/peps/pep-3123/) 並使用明確的 `PyObject ob_base;` 欄位 (而非`PyObject_HEAD`)，然而基於回溯相容性的理由，不一定總是可行。

### <a name="native-values-view-in-python-code"></a>Python 程式碼中的原生值檢視

類似于上一節，當 Python 框架為使用中時，您可以在 [**區域變數**] 視窗中為原生值啟用 **[c + + view]** 。 此功能預設為未啟用，請以滑鼠右鍵按一下 [區域變數] 視窗，然後切換 [Python] > [顯示 C++ 檢視節點] 功能表選項來開啟它。

![在 [區域變數] 視窗中啟用 [C++ 檢視]](media/mixed-mode-debugging-enable-cpp-view.png)

**[C + + view]** 節點提供值的基礎 C/c + + 結構的標記法，與您在原生框架中看到的值完全相同。 比方說，它會顯示 Python 長整數的 `_longobject` (`PyLongObject` 是其 typedef) 執行個體，而且會嘗試推斷您自行撰寫之原生類別的類型。 此節點的子系是可編輯的。

![[區域變數] 視窗中的 [C++ 檢視]](media/mixed-mode-debugging-cpp-view.png)

如果物件的子欄位屬於類型 `PyObject` 或其他支援的類型之一，則它會有 **[Python view]** 表示節點 (如果已啟用這些表示) ，則可以導覽不會直接對 Python 公開連結的物件圖形。

不同于 **[python view]** 節點（使用 python 物件中繼資料來判斷物件的類型），沒有類似的可靠機制可進行 **[c + + view]**。 一般而言，憑藉一個 Python 值 (也就是 `PyObject` 參考) 是無法可靠地判斷支援它的 C/C++ 結構。 混合模式偵錯工具會透過查看具有函式指標類型的物件類型 (例如其 `ob_type` 欄位參考的 `PyTypeObject`) 的各個欄位，以嘗試猜測該類型 。 如果這些函式指標之一參考的函式可以解析，而且該函式具有類型比 `PyObject*` 更明確的 `self` 參數，則會假設該類型為支援的類型。 例如，如果是下列函式中指定物件點的 `ob_type->tp_init`︰

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

則偵錯工具可以正確地推論出物件的 C 類型是 `FobObject`。 如果無法從 `tp_init` 判斷更精確的類型，它會繼續嘗試其他欄位。 如果無法從任何欄位推算類型， **[c + + view]** 節點會將物件呈現為 `PyObject` 實例。

為了始終能夠取得自訂撰寫類型最有用的表示法，註冊類型時最好註冊至少一個特殊函式，並使用強型別 `self` 參數。 大多數類型都能自然地滿足該需求；若非如此，`tp_init` 通常是針對此用途最方便使用的項目。 虛構的 `tp_init` 實作只能立即傳回零，它適用於為啟用偵錯工具類型推斷而存在的類型，如上面的程式碼範例所示。

## <a name="differences-from-standard-python-debugging"></a>與標準 Python偵錯的差異

混合模式偵錯工具與[標準 Python 偵錯工具](debugging-python-in-visual-studio.md)的不同之處在於它導入一些額外功能，但缺少一些 Python 相關功能︰

- 不支援的功能：條件中斷點、 **Debug 互動式** 視窗和跨平臺遠端偵錯。
- 即時 **運算視窗：** 可供使用，但其功能的子集有限，包括此處所列的所有限制。
- 支援的 Python 版本︰僅限 CPython 2.7 和 3.3 及更新版本。
- Visual Studio Shell︰搭配使用 Python 和 Visual Studio Shell 時 (例如使用整合式安裝程式進行安裝時)，Visual Studio 無法開啟 C++ 專案，且針對 C++ 檔案的編輯體驗僅如同使用基本文字編輯器。 不過，Shell 搭配偵錯工具視窗中的原始程式碼、逐步執行到原生程式碼及 C++ 運算式評估，可完整支援 C/C++ 偵錯和混合模式偵錯。
- 視圖和展開物件：當您在 [ **區域變數** **] 和 [監看** 式偵錯工具] 視窗中查看 Python 物件時，混合模式偵錯工具只會顯示物件的結構。 它不會自動評估屬性，或顯示計算的屬性。 對於集合，它只會顯示內建集合類型的元素 (`tuple`、`list``dict``set`)。 自訂集合類型不會視覺化為集合，除非它們繼承自某些內建的集合類型。
- 運算式評估：請參閱下文。

### <a name="expression-evaluation"></a>運算式評估

當偵錯工具在程式碼中的任何時間點暫停時，標準 Python 偵錯工具可讓您在 **監看****式和即時** 運算視窗中評估任意的 python 運算式，只要在 i/o 作業或其他類似的系統呼叫中不會被封鎖。 在混合模式偵錯，任意的運算式只能在 Python 程式碼中停止時、中斷點之後，或逐步執行程式碼時進行評估。 只能在發生中斷點或逐步執行作業的執行緒上評估運算式。

在原生程式碼或在 Python 程式碼 (當上述條件不適用時) 中停止時 (例如，在跳離作業之後，或在不同的執行緒上)，運算式評估僅限於存取目前所選框架範圍中的區域和全域變數、存取其欄位，及為含有常值的內建集合類型編製索引。 例如，下列運算式可在任何內容中評估 (前提是所有識別項參考適當類型的現有變數和欄位)︰

```python
foo.bar[0].baz['key']
```

混合模式偵錯工具也會以不同方式解析這類運算式。 所有成員存取作業都只會查閱直屬於物件的欄位 (例如在其 `__dict__` 或 `__slots__` 中的項目，或透過 `tp_members` 向 Python 公開的原生結構的欄位)，並忽略任何 `__getattr__`、`__getattribute__` 或描述元邏輯。 同樣地，所有編制索引作業會忽略 `__getitem__`，而直接存取集合的內部資料結構。

為保持一致性，此名稱解析配置會使用在所有符合限制的運算式評估條件約束的運算式，不論目前的停止點是否允許任意運算式。 若要在有功能完整的評估工具時強制適當的 Python 語意，請將運算式括在括號中︰

```python
(foo.bar[0].baz['key'])
```
