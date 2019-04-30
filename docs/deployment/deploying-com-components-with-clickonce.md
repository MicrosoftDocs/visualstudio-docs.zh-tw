---
title: 使用 ClickOnce 部署 COM 元件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7032ec5ae03febf6c54978020379769ac742a136
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406631"
---
# <a name="deploy-com-components-with-clickonce"></a>使用 ClickOnce 部署 COM 元件
部署舊版的 COM 元件一直是困難的工作。 元件必須全域註冊，因此可能會導致非預期的副作用之間重疊的應用程式。 這種情況通常不是問題在.NET Framework 應用程式中的因為都是完全隔離的應用程式或元件並排顯示相容。 Visual Studio 可讓您部署隔離的 COM 元件，在 Windows XP 或更高版本的作業系統上。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 提供簡單而安全的機制，可部署您的.NET 應用程式。 不過，如果您的應用程式會使用傳統的 COM 元件，您必須採取額外的步驟，才能將其部署。 本主題描述如何部署隔離的 COM 元件，並參考原生元件 (例如，從 Visual Basic 6.0 或視覺效果C++)。

 如需有關如何部署隔離的 COM 元件的詳細資訊，請參閱 < [Simplify App Deployment with ClickOnce 和免註冊 COM](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx)。

## <a name="registration-free-com"></a>免註冊 COM
 免註冊 COM 是一種新的技術來部署和啟動獨立的 COM 元件。 其運作方式是將所有元件的型別程式庫和註冊資訊通常安裝在系統登錄中的資訊清單的 XML 檔案放在與應用程式相同的資料夾中儲存。

 隔離的 COM 元件需要它註冊為開發人員電腦上，但它並沒有使用者的電腦上註冊。 若要隔離的 COM 元件，您只需要設定它的參考**隔離**屬性設 **，則為 True**。 根據預設，這個屬性設定為**False**，指出，它應該視為已註冊的 COM 參考。 如果這個屬性是 **，則為 True**，它會在建置時，此元件產生資訊清單。 它也會導致在安裝期間，應用程式資料夾複製對應的檔案。

 當資訊清單產生器遇到隔離的 COM 參考時，它會列舉所有`CoClass`中元件的型別程式庫，比對每個項目，其對應的登錄資料，以及產生的項目資訊清單定義所有 com類型程式庫檔案中的類別。

## <a name="deploy-registration-free-com-components-using-clickonce"></a>使用 ClickOnce 免註冊 COM 元件的部署
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署技術非常適合部署隔離的 COM 元件，因為兩者[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]和免註冊 COM 需要元件有資訊清單，以便部署。

 一般而言，元件作者應該提供資訊清單。 如果沒有，不過，Visual Studio 是能夠產生自動為 COM 元件的資訊清單。 資訊清單產生期間，會執行[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]發行程序; 如需詳細資訊，請參閱 <<c2> [ 發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)。 這項功能也可讓您充分利用您先前的開發環境，例如 Visual Basic 6.0 中撰寫的舊版元件。

 有兩種方式，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署 COM 元件：

- 使用啟動載入器來部署您的 COM 元件;這適用於所有支援的平台。

- 使用原生元件隔離 (也稱為免註冊 COM) 部署。 不過，這會只適用於 Windows XP 或更高版本的作業系統。

### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>隔離和部署簡單的 COM 元件的範例
 為了示範免註冊 COM 元件的部署，此範例會參考使用 Visual Basic 6.0 中，建立外掛式原生 COM 元件的 Visual Basic 中建立以 Windows 為基礎的應用程式，並將它使用部署[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]。

 首先，您必須建立原生的 COM 元件：

##### <a name="to-create-a-native-com-component"></a>若要建立原生的 COM 元件

1. 從使用 Visual Basic 6.0**檔案**功能表上，按一下**新增**，然後**專案**。

2. 在 **新的專案**對話方塊中，選取**Visual Basic**節點，然後選取**ActiveX DLL**專案。 在 [名稱] 方塊中，輸入 `VB6Hello`。

    > [!NOTE]
    > 只有 ActiveX DLL 和 ActiveX 控制項的專案類型所支援的免註冊 COM;不支援 ActiveX EXE 和 ActiveX 文件的專案類型。

3. 在 [**方案總管] 中**，按兩下**Class1.vb**開啟文字編輯器。

4. Class1.vb 中新增下列程式碼之後產生的程式碼`New`方法：

    ```vb
    Public Sub SayHello()
       MsgBox "Message from the VB6Hello COM component"
    End Sub
    ```

5. 建置元件。 從**建置**功能表上，按一下**建置方案**。

> [!NOTE]
> 免註冊 COM 支援只 Dll 和 COM 控制項專案類型。 您無法使用 Exe 免註冊 com。

 現在您可以建立以 Windows 為基礎的應用程式，並加入 COM 元件的參考。

##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>若要建立以 Windows 為基礎的應用程式使用 COM 元件

1. 使用 Visual Basic 中，從**檔案**功能表上，按一下**新增**，然後**專案**。

2. 在 **新的專案**對話方塊中，選取**Visual Basic**節點，然後選取**Windows 應用程式**。 在 [名稱] 方塊中，輸入 `RegFreeComDemo`。

3. 在 **方案總管 中**，按一下**顯示所有檔案** 按鈕以顯示專案參考。

4. 以滑鼠右鍵按一下**參考**節點，然後選取**加入參考**從內容功能表。

5. 在 [**加入參考**] 對話方塊中，按一下**瀏覽**索引標籤上，瀏覽至 VB6Hello.dll，然後選取它。

    A **VB6Hello**參考出現在 [參考] 清單中。

6. 指向**工具箱**，選取** 按鈕**控制項，並將它拖曳至**Form1**表單。

7. 在 [**屬性**] 視窗中，將按鈕的**文字**屬性設**Hello**。

8. 按兩下按鈕以新增處理常式程式碼，並在程式碼檔案中，加入程式碼，讓處理常式，如下所示：

   ```vb
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim VbObj As New VB6Hello.Class1
       VbObj.SayHello()
   End Sub
   ```

9. 執行應用程式。 從**偵錯**功能表上，按一下**開始偵錯**。

   接著，您必須找出控制項。 每個應用程式所使用的 COM 元件會在您的專案中顯示 COM 參考。 這些參考會顯示於下方**參考**中的節點**方案總管 中**視窗。 (請注意，您可以將參考直接使用**加入參考**命令**專案** 功能表中，或直接藉由將 ActiveX 控制項拖曳至表單。)

   下列步驟示範如何隔離的 COM 元件，並發佈更新的應用程式隔離的控制項：

##### <a name="to-isolate-a-com-component"></a>隔離的 COM 元件

1. 在 **方案總管**，請在**參考**節點中，選取**VB6Hello**參考。

2. 中**屬性** 視窗中，變更的值**隔離**屬性從**False**來**True**。

3. 從**建置**功能表上，按一下**建置方案**。

   現在，您按下 f5 鍵，應用程式如預期般運作，，但是現在正在免註冊 com。 為了證明這點，請嘗試取消註冊 VB6Hello.dll 元件，並執行 Visual Studio IDE 外部 RegFreeComDemo1.exe。 按一下按鈕時，這次它仍能運作。 如果您暫時重新命名應用程式資訊清單，它會一次失敗。

> [!NOTE]
> 您可以暫時將它取消登錄，以模擬 COM 元件不存在。 開啟命令提示字元中，移至您的系統資料夾中，輸入`cd /d %windir%\system32`，然後輸入，以取消註冊元件`regsvr32 /u VB6Hello.dll`。 您可以再次註冊輸入`regsvr32 VB6Hello.dll`。

 最後一個步驟是發佈應用程式使用[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:

##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>若要發佈應用程式更新與隔離的 COM 元件

1. 從**建置**功能表上，按一下**發佈 RegFreeComDemo**。

    [發行精靈] 隨即出現。

2. 在 [發行精靈] 中，請在本機電腦的磁碟，您可以在此存取，並檢查已發行的檔案中指定的位置。

3. 按一下 [完成] 發佈應用程式。

   如果您檢查已發行的檔案時，您會發現 sysmon.ocx 檔案包含。 控制項是控制項的完全隔離，此應用程式，這表示，如果終端使用者的電腦上有另一個應用程式使用不同版本，它不會干擾此應用程式。

## <a name="reference-native-assemblies"></a>參考原生組件
 Visual Studio 支援原生的 Visual Basic 6.0 的參考或C++組件;這類參考，會呼叫原生參考。 您可以分辨是否參考為原生驗證其**檔案類型**屬性設定為**原生**或是**ActiveX**。

 若要新增的原生的參考，請使用**加入參考**命令，然後瀏覽至資訊清單。 某些元件會放置在 DLL 內的資訊清單。 在此情況下，您可以只選擇該 DLL 本身，而且 Visual Studio 會將它新增為原生參考如果它偵測到此元件包含內嵌的資訊清單。 Visual Studio 也會自動將任何相依的檔案或組件資訊清單中所列，如果它們是在與參考的元件相同的資料夾。

 COM 控制項隔離可讓您更輕鬆地部署還沒有資訊清單的 COM 元件。 不過，如果元件提供使用資訊清單中，您可以直接參考的資訊清單。 事實上，您應該一律使用而不是使用可能的話，元件作者所提供的資訊清單**隔離**屬性。

## <a name="limitations-of-registration-free-com-component-deployment"></a>免註冊 COM 元件部署的限制
 免註冊 COM 提供明顯的優點，透過傳統部署技術。 不過，有幾點限制和也必須指出的注意事項。最大限制是，它只適用於 Windows XP 或更高版本。 免註冊 COM 的實作需要對核心作業系統中載入元件的方式變更。 不幸的是，沒有免註冊 COM 支援舊版層

 不是每個元件是免註冊 COM 的適當候選項目 如果下列任一項成立，就不適合元件：

- 元件是跨處理序伺服器。 不支援 EXE 伺服器;支援只 Dll。

- 該元件是作業系統的一部分，或系統元件，例如 XML、 Internet Explorer 或 Microsoft Data Access Components (MDAC)。 您應該遵循元件作者; 的重新發佈原則請連絡廠商。

- 元件是應用程式，例如 Microsoft Office 的一部分。 例如，您應該嘗試找出 Microsoft Excel 物件模型。 這是 Office 的一部分，並只能在電腦上安裝完整的 Office 產品。

- 元件被為了做為增益集或嵌入式管理單元，例如 Office 增益集或網頁瀏覽器中的控制項。 這類元件通常需要某種類型的已超出範圍的資訊清單本身的裝載環境所定義的註冊配置。

- 元件會管理系統，例如，列印多工緩衝處理器的裝置驅動程式的實體或虛擬裝置。

- 元件為資料存取可轉散發套件。 資料應用程式通常需要不同資料存取的可轉散發套件才能執行安裝。 您不應該嘗試隔離元件，例如 Microsoft ADO 資料控制項、 Microsoft OLE DB 或 Microsoft Data Access Components (MDAC)。 相反地，如果您的應用程式使用 MDAC 或 SQL Server Express，您應該將它們設為必要條件。請參閱[How to:使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)。

  在某些情況下，它可能會重新設計免註冊 COM 元件的開發人員 如果這不可行，但您仍會建置，並發佈應用程式，透過使用啟動載入器的標準註冊配置相依於這些。 如需詳細資訊，請參閱 <<c0> [ 建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)。

  COM 元件只能一次隔離，每個應用程式。 比方說，您無法將相同的 COM 元件，從兩個不同的隔離**類別庫**屬於相同的應用程式的專案。 這樣會導致建置警告，以及應用程式將無法在執行階段載入。 若要避免這個問題，Microsoft 會建議您將封裝單一類別庫中的 COM 元件。

  即使應用程式的部署不需要註冊，則需要有 com 必須註冊開發人員的電腦的幾個案例。 `Isolated`屬性需要開發人員的電腦上註冊 COM 元件，以自動產生資訊清單在建置期間。 沒有註冊擷取的功能，在建置期間叫用自我登錄。 此外，任何未明確定義型別程式庫中的類別不會反映在資訊清單中。 使用既有的資訊清單，例如原生參考的 COM 元件時可能不會註冊在開發期間需要的元件。 不過，就必須註冊如果元件是以 ActiveX 控制項，而且您想要將它併入**工具箱**和 Windows Form 設計工具。

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)