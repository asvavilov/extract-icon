unit Unit1;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, ShellAPI, StdCtrls, ExtCtrls, ComCtrls,
  FileCtrl, ExtDlgs, RXCtrls;

type
  TForm1 = class(TForm)
    OpenDialog1: TOpenDialog;
    Button1: TButton;
    Image1: TImage;
    UpDown1: TUpDown;
    FileListBox1: TFileListBox;
    DirectoryListBox1: TDirectoryListBox;
    DriveComboBox1: TDriveComboBox;
    SavePictureDialog1: TSavePictureDialog;
    Save: TButton;
    RxLabel1: TRxLabel;
    RxLabel2: TRxLabel;
    procedure Button1Click(Sender: TObject);
    procedure UpDown1Click(Sender: TObject; Button: TUDBtnType);
    procedure FileListBox1Change(Sender: TObject);
    procedure FileListBox1KeyDown(Sender: TObject; var Key: Word;
      Shift: TShiftState);
    procedure DirectoryListBox1Change(Sender: TObject);
    procedure SaveClick(Sender: TObject);
  private
    procedure DrawI;
    { Private declarations }
  public
    { Public declarations }
  end;

var
  Form1: TForm1;
  ii: integer;
  fn: String;
  hi: HICON;

implementation

{$R *.dfm}

procedure TForm1.Button1Click(Sender: TObject);
begin
OpenDialog1.Execute;
fn:=OpenDialog1.FileName;
ii:=-1;
hi:=ExtractIcon(hInstance,PAnsiChar(fn),ii);
Button1.Caption:='Всего иконок - '+inttostr(hi);
updown1.Max:=hi-1;
if hi=0 then updown1.Max:=0;
updown1.Position:=0;
ii:=0;
DrawI;
end;

procedure TForm1.DrawI;
begin
ii:=updown1.Position;
hi:=ExtractIcon(hInstance,PAnsiChar(fn),ii);
Image1.Picture.Icon.Handle:=hi;
application.Icon.Handle:=hi;
form1.Caption:=' - иконка №'+inttostr(ii);
updown1.Refresh;
end;

procedure TForm1.UpDown1Click(Sender: TObject; Button: TUDBtnType);
begin
DrawI;
end;

procedure TForm1.FileListBox1Change(Sender: TObject);
begin
fn:=FileListBox1.FileName;
ii:=-1;
hi:=ExtractIcon(hInstance,PAnsiChar(fn),ii);
Button1.Caption:='Всего иконок - '+inttostr(hi);
updown1.Max:=hi-1;
if hi=0 then updown1.Max:=0;
updown1.Position:=0;
ii:=0;
DrawI;
end;

procedure TForm1.FileListBox1KeyDown(Sender: TObject; var Key: Word;
  Shift: TShiftState);
begin
if Key=vk_left then
begin
updown1.Position:=pred(updown1.Position);
key:=0
end;
if Key=vk_right then
begin
updown1.Position:=succ(updown1.Position);
key:=0
end;
DrawI;
end;

procedure TForm1.DirectoryListBox1Change(Sender: TObject);
begin
//filelistbox1.Directory:=directorylistbox1.Directory;

end;

procedure TForm1.SaveClick(Sender: TObject);
begin
if (image1.Picture.Icon.Handle=0) then exit;
if (not(savepicturedialog1.Execute)) then exit;
image1.Picture.Icon.SaveToFile(savepicturedialog1.FileName);
end;

end.
