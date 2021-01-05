---
title: 快速入門 - 開啟 Python 程式碼資料夾
description: 您可以在此快速入門中，從資料夾開啟並執行 Python 程式碼，不需使用 Visual Studio 專案 (僅限 Visual Studio 2019)。
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: d11ffcb2c43d2c519d75d43afad6383e0bfaa44a
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761273"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>快速入門：開啟並執行資料夾中的 Python 程式碼

[在 Visual Studio 2019 中安裝 Python 支援](installing-python-support-in-visual-studio.md)之後，就可以很容易地在 Visual Studio 2019 中執行現有的 Python 程式碼，不需要建立 Visual Studio 專案。

> [!Note]
> Visual Studio 2017 及舊版會要求您建立 Visual Studio 專案以執行 Python 程式碼，使用內建專案範本即可輕鬆執行。 請參閱 [快速入門：從現有程式碼建立 Python 專案](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. 您可以在此逐步解說中，使用包含所需 Python 程式碼的任何資料夾。 若要依照這裡的範例進行，請使用命令 `git clone https://github.com/gregmalcolm/python_koans` 將 gregmalcolm/python_koans GitHub 存放庫複製到您的電腦的適當資料夾中。

1. 啟動 Visual Studio 2019，並在 [開始] 視窗中，選取 [開始使用] 資料行底部的 [開啟]。 或者，如果您已經有 Visual Studio 正在執行，請改 **為選取**[  >  **開啟**  >  **資料夾**] 命令。

    ![Visual Studio 啟動畫面](media/quickstart-open-folder/01-open-local-folder.png)

1. 瀏覽至包含 Python 程式碼的資料夾，然後選擇 [選取資料夾]。 如果您正在使用 python_koans code，請確定選取複製資料夾內的 `python3` 資料夾。

    ![[開啟資料夾] 命令的 [選取資料夾] 對話方塊](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio 會在 [方案總管] 中名為 [資料夾檢視] 的區段顯示資料夾。 您可以使用位於資料夾名稱左邊邊緣的箭號展開及摺疊資料夾：

    ![[方案總管] 中可用於展開及摺疊資料夾的控制項](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. 開啟 Python 資料夾時，Visual Studio 會建立數個隱藏的資料夾，用於管理專案的相關設定。 若要查看這些資料夾 (以及任何其他隱藏的檔案和資料夾，例如 *.git* 資料夾)，請選取 [顯示所有檔案] 工具列按鈕：

    ![[方案總管] 中隱藏資料夾的檢視](media/quickstart-open-folder/05-view-hidden-folders.png)

1. 若要執行程式碼，必須先識別啟動或主要的程式檔案。 在這裡顯示的範例中，啟動檔案為 *contemplate-koans.py*。 以滑鼠右鍵按一下該檔案並選取 [設定為啟動項目]。

    ![在 [方案總管] 中設定啟動項目](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > 如果啟動項目不在所開啟資料夾的根目錄中，您也必須依照[設定工作目錄](#set-a-working-directory)一節中所述，在啟動組態 JSON 檔案中加入一行。

1. 按下 **Ctrl** + **F5** 或選取 [不使用 **偵錯工具** 來  >  **啟動**]，以執行程式碼。 您也可以選取以播放按鈕方式顯示啟動項目的工具列按鈕，這會在 Visual Studio 偵錯工具中執行程式碼。 在所有情況下，Visual Studio 都會偵測您的啟動項目是 Python 檔案，所以會自動在預設的 Python 環境中執行程式碼。 (該環境會顯示在工具列上啟動項目的右邊。)

    ![啟動偵錯工具工具列按鈕](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. 程式的輸出會顯示在個別命令視窗中：

    ![用於執行 Python 程式碼的輸出視窗](media/quickstart-open-folder/08-result-window.png)

1. 若要在其他環境中執行程式碼，請從工具列上的下拉式清單控制項選取環境，然後再度啟動啟動項目。

1. 若要關閉 Visual Studio 中的資料夾，請 **選取 [檔案**  >  **關閉資料夾**] 功能表命令。

## <a name="set-a-working-directory"></a>設定工作目錄

根據預設，Visual Studio 會以同一資料夾根目錄中資料夾的方式執行開啟的 Python 專案。 但是，專案中的程式碼可能會假設 Python 正在子資料夾中執行。 例如，假設您開啟 python_koans 存放庫的根資料夾，然後設定 *python3/contemplate-koans.py* 檔案作為啟動項目。 如果您之後執行程式碼，會發生找不到 *koans.txt* 檔案的錯誤。 發生這個錯誤的原因是因為 *contemplate-koans.py* 假設 Python 正在 *python3* 資料夾 (而不是在存放庫根目錄 ) 中執行。

在此情況下，您也必須在啟動組態 JSON 檔案中新增一行以指定工作目錄：

1. 在 [方案總管] 中以滑鼠右鍵按一下 Python (*.py*) 啟動檔案，並選取 [偵錯並啟動設定]。

    ![已選取 contemplate-koans.py 檔案，以及在操作功能表上選取 [偵錯工具] 和 [啟動] 設定的方案總管資料夾檢視螢幕擷取畫面。](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. 在顯示的 [選取偵錯工具] 對話方塊中，依序選取 [預設] 和 [選取]。

    ![[選取偵錯工具] 對話方塊的螢幕擷取畫面，其中選取了 [預設偵錯工具] 並選擇 [選取] 按鈕。](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > 如果您沒有看到 [**預設值**] 選擇，請在選取 [ **Debug and 啟動設定**] 命令時，確定您已選擇 *.py* 檔案。 Visual Studio 會使用檔案類型來決定要顯示的偵錯工具選項。

1. Visual Studio 會開啟位於隱藏的 *.vs* 資料夾中，名為 *launch.vs.json* 的檔案。 此檔案會描述專案的偵錯內容。 若要指定工作目錄，請 `"workingDirectory"` 的值，如 python-koans 範例的 `"workingDirectory": "python3"` 所示：

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. 儲存檔案並再次啟動程式，它現在會在指定的資料夾中執行。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [教學課程：在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>請參閱

- [快速入門：從現有程式碼建立 Python 專案](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [快速入門：從存放庫建立 Python 專案](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [手動識別現有的 Python 解譯器](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
