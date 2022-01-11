# ControlTower
AWSサービス（AWS Organizations、AWS Service Catalog、AWSシングルサインオンを含む）を使用して、landingZoneを1時間未満で構築できます。リソースは、ユーザーに代わって設定および管理されます。




## Control Tower構築時
### CTとConfigの問題
- 実際検証してみて
  - Config設定を削除しなくてもエラーにならない
  - 既存Config設定を維持しつつ、CTの有効化可能

### CTとTrailの問題
- 既存の証跡があってもエラーにならない
- 既存とCT後新規証跡で二重に証跡が取られるためコストがかかる

### CTとSSOの問題
- CT有効と同時にSSOも構築される
- 事前にSSO構築しておくことも可能
