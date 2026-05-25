# DGF Connect — CI/CD

Public repo chứa GitHub Actions workflow cho project DGF Connect.

> Source code ứng dụng được lưu trữ **private trên GitLab** và được clone vào runner trong quá trình build — không có source code nào trong repo này.

## Cách hoạt động

```
Developer chạy deploy.sh (trên máy local)
    → push tag lên GitLab
    → trigger workflow tại repo này qua GitHub API

GitHub Actions runner:
    ├── Job Android (ubuntu-latest)
    │     clone source từ GitLab → build APK + AAB
    │     → Firebase App Distribution (dev & prod)
    │     → Google Play Closed Testing (prod only)
    │
    └── Job iOS (macos-latest)
          clone source từ GitLab → build IPA
          → TestFlight (dev & prod)
```

## Trigger

Workflow được trigger tự động qua `workflow_dispatch` từ script `deploy.sh` trong project GitLab.
Có thể trigger thủ công tại tab **Actions → Build & Deploy → Run workflow**.

## Secrets yêu cầu

Xem hướng dẫn đầy đủ tại `DEPLOYMENT_GUIDE.md` trong project GitLab.
