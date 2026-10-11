# Vercel Latency Analytics API

## Deploy
1. Upload this entire folder to a GitHub repository (keep `api/`, `requirements.txt`,
   `vercel.json`, and `q-vercel-latency.json` at the repository root as shown).
2. Import the repository into Vercel and deploy.
3. Test with a POST request to `https://YOUR-DEPLOYMENT.vercel.app/`.

## Example request
```json
{
  "regions": ["apac", "emea"],
  "threshold_ms": 160
}
```

## CORS
FastAPI CORS middleware allows any origin, POST and OPTIONS, and all request headers.
Credentials are disabled because wildcard origins and credentialed requests are not
compatible under standard browser CORS rules. For this assignment's JSON POST request,
browsers may send an OPTIONS preflight; the middleware handles it.

## Windows PowerShell test
```powershell
$body = @{
    regions = @("apac", "emea")
    threshold_ms = 160
} | ConvertTo-Json

Invoke-RestMethod -Uri "https://YOUR-DEPLOYMENT.vercel.app/" `
  -Method Post -ContentType "application/json" -Body $body
```
