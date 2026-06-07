# Runbook: Deployment Failed

## Trigger
GitHub Actions pipeline fails

## Impact
New features not deployed, old version still running

## Steps
1. Check GitHub Actions logs for exact error
2. Rollback immediately:
   kubectl rollout undo deployment/placemux-app
3. Verify rollback successful:
   curl /health → expect 200 OK
4. Fix issue in code
5. Test on staging first
6. Redeploy after fix confirmed