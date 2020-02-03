---
title: Hospedando conteúdo Win32
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: b3113d9f3146e1590363dc9db6f751a429dda74b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747019"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="d674d-102">Hospedando conteúdo Win32 no WPF</span><span class="sxs-lookup"><span data-stu-id="d674d-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d674d-103">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d674d-103">Prerequisites</span></span>

<span data-ttu-id="d674d-104">Consulte [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="d674d-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="d674d-105">Um passo a passo do Win32 no Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="d674d-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="d674d-106">Para reutilizar o conteúdo Win32 dentro de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos, use <xref:System.Windows.Interop.HwndHost>, que é um controle que torna os HWNDs semelhantes a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d674d-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="d674d-107">Assim como o <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> é simples de usar: derive de <xref:System.Windows.Interop.HwndHost> e implemente os métodos `BuildWindowCore` e `DestroyWindowCore` e, em seguida, instancie sua classe derivada de <xref:System.Windows.Interop.HwndHost> e coloque-a dentro de seu aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d674d-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="d674d-108">Se a lógica do Win32 já estiver empacotada como um controle, então sua implementação de `BuildWindowCore` será pouco mais do que uma chamada para `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="d674d-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="d674d-109">Por exemplo, para criar um controle LISTBOX do Win32 C++no:</span><span class="sxs-lookup"><span data-stu-id="d674d-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

<span data-ttu-id="d674d-110">Mas suponha que o código Win32 não seja tão independente?</span><span class="sxs-lookup"><span data-stu-id="d674d-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="d674d-111">Nesse caso, você pode criar uma caixa de diálogo do Win32 e inserir seu conteúdo em um aplicativo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] maior.</span><span class="sxs-lookup"><span data-stu-id="d674d-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="d674d-112">O exemplo mostra isso no Visual Studio e C++, embora também seja possível fazer isso em um idioma diferente ou na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d674d-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="d674d-113">Comece com uma caixa de diálogo simples, que é compilada em um projeto de C++ dll.</span><span class="sxs-lookup"><span data-stu-id="d674d-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="d674d-114">Em seguida, coloque a caixa de diálogo no aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] maior:</span><span class="sxs-lookup"><span data-stu-id="d674d-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="d674d-115">Compilar a DLL como gerenciada (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="d674d-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="d674d-116">Transforme a caixa de diálogo em um controle</span><span class="sxs-lookup"><span data-stu-id="d674d-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="d674d-117">Definir a classe derivada de <xref:System.Windows.Interop.HwndHost> com os métodos `BuildWindowCore` e `DestroyWindowCore`</span><span class="sxs-lookup"><span data-stu-id="d674d-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="d674d-118">Substitua o método `TranslateAccelerator` para manipular as teclas do diálogo</span><span class="sxs-lookup"><span data-stu-id="d674d-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="d674d-119">Substitua o método `TabInto` para dar suporte à tabulação</span><span class="sxs-lookup"><span data-stu-id="d674d-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="d674d-120">Substitua o método `OnMnemonic` para dar suporte aos mnemônicos</span><span class="sxs-lookup"><span data-stu-id="d674d-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="d674d-121">Crie uma instância da subclasse <xref:System.Windows.Interop.HwndHost> e coloque-a sob o elemento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à direita</span><span class="sxs-lookup"><span data-stu-id="d674d-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="d674d-122">Transforme a Caixa de Diálogo em um Controle</span><span class="sxs-lookup"><span data-stu-id="d674d-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="d674d-123">Você pode transformar uma caixa de diálogo em um HWND filho usando os estilos WS_CHILD e DS_CONTROL.</span><span class="sxs-lookup"><span data-stu-id="d674d-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="d674d-124">Vá para o arquivo de recurso (.rc) no qual a caixa de diálogo está definida e localize o início da definição da caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="d674d-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="d674d-125">Altere a segunda linha para:</span><span class="sxs-lookup"><span data-stu-id="d674d-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="d674d-126">Essa ação não o empacota totalmente em um controle independente; Você ainda precisa chamar `IsDialogMessage()` para que o Win32 possa processar determinadas mensagens, mas a alteração de controle fornece uma maneira simples de colocar esses controles dentro de outro HWND.</span><span class="sxs-lookup"><span data-stu-id="d674d-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="d674d-127">Subclasse HwndHost</span><span class="sxs-lookup"><span data-stu-id="d674d-127">Subclass HwndHost</span></span>

<span data-ttu-id="d674d-128">Importe os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="d674d-128">Import the following namespaces:</span></span>

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

<span data-ttu-id="d674d-129">Em seguida, crie uma classe derivada de <xref:System.Windows.Interop.HwndHost> e substitua os métodos `BuildWindowCore` e `DestroyWindowCore`:</span><span class="sxs-lookup"><span data-stu-id="d674d-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

<span data-ttu-id="d674d-130">Aqui você vai usar o `CreateDialog` para criar a caixa de diálogo que é, na realidade, um controle.</span><span class="sxs-lookup"><span data-stu-id="d674d-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="d674d-131">Como esse é um dos primeiros métodos chamados dentro da DLL, você também deve fazer alguma inicialização padrão do Win32 chamando uma função que você definirá posteriormente, chamada `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="d674d-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="d674d-132">Substitua o método TranslateAccelerator para manipular as teclas do diálogo</span><span class="sxs-lookup"><span data-stu-id="d674d-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="d674d-133">Se executar este exemplo agora, você obterá um controle de caixa de diálogo que exibe, mas ele ignoraria todo o processamento do teclado que torna uma caixa de diálogo funcional.</span><span class="sxs-lookup"><span data-stu-id="d674d-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="d674d-134">Agora, você deve substituir a implementação de `TranslateAccelerator` (que vem de `IKeyboardInputSink`, uma interface que <xref:System.Windows.Interop.HwndHost> implementa).</span><span class="sxs-lookup"><span data-stu-id="d674d-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="d674d-135">Esse método é chamado quando o aplicativo recebe WM_KEYDOWN e WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="d674d-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

<span data-ttu-id="d674d-136">É muito código de uma vez, então as explicações poderiam ser um pouco mais detalhadas.</span><span class="sxs-lookup"><span data-stu-id="d674d-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="d674d-137">Primeiro, o código usando C++ macros e C++ ; Você precisa estar ciente de que já existe uma macro chamada `TranslateAccelerator`, que é definida em winuser. h:</span><span class="sxs-lookup"><span data-stu-id="d674d-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="d674d-138">Certifique-se de definir um método `TranslateAccelerator` e não um método `TranslateAcceleratorW`.</span><span class="sxs-lookup"><span data-stu-id="d674d-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="d674d-139">Da mesma forma, há o winuser.h MSG não gerenciado e o struct `Microsoft::Win32::MSG` gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d674d-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="d674d-140">Você pode desambiguar entre os dois usando C++ o operador de `::`.</span><span class="sxs-lookup"><span data-stu-id="d674d-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}

Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

<span data-ttu-id="d674d-141">Voltar para `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="d674d-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="d674d-142">O princípio básico é chamar a função do Win32 `IsDialogMessage` para fazer o máximo de trabalho possível, mas `IsDialogMessage` não tem acesso a nada fora da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d674d-142">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="d674d-143">Como uma guia de usuário na caixa de diálogo, quando a tabulação passar do último controle na nossa caixa de diálogo, você precisará definir o foco para a parte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamando `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="d674d-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

<span data-ttu-id="d674d-144">Finalmente, chame `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="d674d-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="d674d-145">Mas uma das responsabilidades de um método `TranslateAccelerator` está informando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se você lidou com o pressionamento de teclas ou não.</span><span class="sxs-lookup"><span data-stu-id="d674d-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="d674d-146">Se você não lidou com isso, o evento de entrada poderá criar um túnel e uma bolha pelo resto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d674d-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="d674d-147">Aqui, você vai expor uma peculiaridade da manipulação de messange de teclado e da natureza da arquitetura de entrada no Win32.</span><span class="sxs-lookup"><span data-stu-id="d674d-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="d674d-148">Infelizmente, `IsDialogMessage` não é retornado de nenhuma forma independentemente de lidar ou não com um determinado pressionamento de tecla.</span><span class="sxs-lookup"><span data-stu-id="d674d-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="d674d-149">Ainda pior, ele chamará `DispatchMessage()` nos pressionamentos de teclas que ele não deveria manipular!</span><span class="sxs-lookup"><span data-stu-id="d674d-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="d674d-150">Assim você terá que fazer engenharia reversa de `IsDialogMessage` e apenas chamá-lo para as teclas que você sabe que ele manipulará:</span><span class="sxs-lookup"><span data-stu-id="d674d-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="d674d-151">Substituir o método TabInto para dar suporte à tabulação</span><span class="sxs-lookup"><span data-stu-id="d674d-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="d674d-152">Agora que você implementou `TranslateAccelerator`, um usuário pode tabular dentro da caixa de diálogo caixa e fora dela no aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] maior.</span><span class="sxs-lookup"><span data-stu-id="d674d-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="d674d-153">Mas um usuário não pode tabular novamente na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d674d-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="d674d-154">Para resolver isso, você deve substituir `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="d674d-154">To solve that, you override `TabInto`:</span></span>

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

<span data-ttu-id="d674d-155">O parâmetro `TraversalRequest` informa se a ação da guia é uma guia ou guia de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="d674d-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="d674d-156">Substitua o método OnMnemonic para dar suporte aos mnemônicos</span><span class="sxs-lookup"><span data-stu-id="d674d-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="d674d-157">A manipulação de teclado está quase concluída, mas há uma coisa faltando: os mnemônicos não funcionam.</span><span class="sxs-lookup"><span data-stu-id="d674d-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="d674d-158">Se um usuário pressionar alt-F, o foco não pulará para a caixa de edição “Nome:”.</span><span class="sxs-lookup"><span data-stu-id="d674d-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="d674d-159">Portanto, você substitui o método `OnMnemonic`:</span><span class="sxs-lookup"><span data-stu-id="d674d-159">So, you override the `OnMnemonic` method:</span></span>

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

<span data-ttu-id="d674d-160">Por que não chamar `IsDialogMessage` aqui?</span><span class="sxs-lookup"><span data-stu-id="d674d-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="d674d-161">Você tem o mesmo problema que antes: precisa ser capaz de informar o código [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se seu código manipulou o pressionamento de teclas ou não e `IsDialogMessage` não pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="d674d-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="d674d-162">Há também um segundo problema, pois `IsDialogMessage` se recusará a processar o mnemônico se o HWND com o foco não estiver dentro da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d674d-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="d674d-163">Instanciar a classe derivada de HwndHost</span><span class="sxs-lookup"><span data-stu-id="d674d-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="d674d-164">Por fim, agora que o suporte de chave e guia está em vigor, você pode colocar seu <xref:System.Windows.Interop.HwndHost> no aplicativo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] maior.</span><span class="sxs-lookup"><span data-stu-id="d674d-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="d674d-165">Se o aplicativo principal for escrito em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a maneira mais fácil de colocá-lo no lugar certo é deixar um elemento de <xref:System.Windows.Controls.Border> vazio no qual você deseja colocar o <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="d674d-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="d674d-166">Aqui, você cria um <xref:System.Windows.Controls.Border> chamado `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="d674d-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

<span data-ttu-id="d674d-167">Então, tudo o que resta é encontrar um bom local na sequência de código para criar uma instância do <xref:System.Windows.Interop.HwndHost> e conectá-lo ao <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="d674d-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="d674d-168">Neste exemplo, você irá colocá-lo dentro do construtor para a classe derivada <xref:System.Windows.Window>:</span><span class="sxs-lookup"><span data-stu-id="d674d-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

<span data-ttu-id="d674d-169">O que fornece:</span><span class="sxs-lookup"><span data-stu-id="d674d-169">Which gives you:</span></span>

![Captura de tela do aplicativo WPF em execução.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="d674d-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d674d-171">See also</span></span>

- [<span data-ttu-id="d674d-172">Interoperação do WPF e do Win32</span><span class="sxs-lookup"><span data-stu-id="d674d-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
