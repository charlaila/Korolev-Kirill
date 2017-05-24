unit Unit1;

{$mode objfpc}{$H+}

interface

uses
  Classes, SysUtils, mysql55conn, sqldb, db, FileUtil, Forms, Controls,
  Graphics, Dialogs, DBGrids, StdCtrls;

type

  { TForm1 }

  TForm1 = class(TForm)
    Button1: TButton;
    Button2: TButton;
    Button3: TButton;
    Button4: TButton;
    DataSource1: TDataSource;
    DBGrid1: TDBGrid;
    MySQL55Connection1: TMySQL55Connection;
    SQLQuery1: TSQLQuery;
    SQLTransaction1: TSQLTransaction;
    procedure Button1Click(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure Button3Click(Sender: TObject);
    procedure Button4Click(Sender: TObject);
  private
    { private declarations }
  public
    { public declarations }
  end;

var
  Form1: TForm1;

implementation

{$R *.lfm}

{ TForm1 }

procedure TForm1.Button1Click(Sender: TObject);
begin
   try
   MySQL55Connection1.Connected:=true;
 except
   ShowMessage('Подключение к БД: ОШИБКА!');
   exit;
 end;
end;

procedure TForm1.Button2Click(Sender: TObject);
begin
   try
   SQLTransaction1.Active:=true;
 except
   ShowMessage('Транзакция: ОШИБКА!');
   exit;
 end;
end;

procedure TForm1.Button3Click(Sender: TObject);
  var
    str_sql : string;
begin
  try
   SQLQuery1.Active := false;
   SQLQuery1.SQL.Clear;
   str_sql := 'SET character_set_client='+#39+'utf8'+#39+',character_set_connection='+#39+'cp1251'+#39+',character_set_results='+#39+'utf8'+#39+';';
   SQLQuery1.sql.add(str_sql);
   SQLQuery1.ExecSQL;
   SQLQuery1.SQL.Clear;
   SQLQuery1.sql.add('SELECT * FROM spravochnik;');
   SQLQuery1.Open;
  except
   ShowMessage('SQL-запрос: ОШИБКА!');
   exit;
 end;
end;

procedure TForm1.Button4Click(Sender: TObject);
begin
  SQLQuery1.Active:=false;
  SQLTransaction1.Commit;
  MySQL55Connection1.Connected:=false;
end;
end.

