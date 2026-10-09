# Facilities Companion

**Facilities request and approval management system for Complete Childcare**

Live: https://alechodson.github.io/facilities-companion/

## Overview

Facilities Companion is a complete facilities request and approval management system that enables nursery managers to submit facility change requests, which are then routed through a dynamic approval chain based on cost and labour requirements.

## Key Features

### Dynamic Approval Routing

Requests are automatically routed to the appropriate approval chain based on cost and labour estimates:

- **Route A** (Simple): Cost ≤ £500 AND Labour ≤ 5 days → Simon Hasler only
- **Route B** (Standard): Cost > £500 OR Labour > 5 days → Simon → Emma → Alec
- **Route C** (Complex): Cost > £2,500 AND Labour > 10 days → Simon → Emma → Alec (flagged)

### Complete Approval Workflow

- **Approve**: Move request to next approver in chain
- **Request Revision**: Send back to requestor with feedback; route recalculates on resubmit
- **Reject**: Decline request (terminal state)

### Full Dashboards

- **Requestor Dashboard**: View own requests, track approval progress
- **Approver Dashboard**: See all requests across all nurseries (complete transparency)
- **Area Manager Dashboard**: View zone-filtered requests
- **All Requests View**: Comprehensive view with filtering by status, zone, priority

### PO Code Generation

Automatic PO code generation on final approval:
- Format: `{NURSERY_CODE}-{I/E}{RESOURCE_CODE}-{PRIORITY}`
- Example: `KCL-EMAINT-2` (Kingsclere, External Maintenance, High Priority)

### Additional Features

- Automatic archival on completion
- Complete approval history with timestamps
- Auto-escalation framework (5 business day trigger)
- Email notification framework (ready for Outlook integration)
- Role-based visibility
- Responsive design (desktop and mobile)

## Authentication

Three sign-in methods:

1. **Automatic** (Teams or Browser): If already signed into M365
2. **One-click**: "Sign in with Microsoft 365" button
3. **Manual**: Select identity from dropdown picker

Uses Microsoft Entra SSO (CCG Ops Triage app)

## Data Storage

**MVP**: Browser localStorage (for testing)
**Production**: SharePoint Graph API (FacilitiesRequests folder)

## Technical Stack

- **Frontend**: Vanilla JavaScript (no frameworks)
- **Hosting**: GitHub Pages (static)
- **Auth**: MSAL 2.30.0
- **Teams**: Teams SDK 2.11.0
- **File Size**: 92.5 KB (single HTML file)

## Deployment

The app is deployed to GitHub Pages and live at:
https://alechodson.github.io/facilities-companion/

### GitHub Pages Cache

Changes may take 1-2 minutes to reflect. Use cache-busting query parameter if needed:
https://alechodson.github.io/facilities-companion/?v=1

## Testing

### Test Accounts

- **Simon Hasler** (Approver): simon.hasler@completechildcare.co.uk
- **Emma McIntyre** (Approver): emma.mcintyre@completechildcare.co.uk
- **Alec Hodson** (Approver): alec.hodson@completechildcare.co.uk
- **Pav Bilkhu** (Area Manager, BlueWater): pav.bilkhu@completechildcare.co.uk
- **Leanne Maynard** (Area Manager, Greenwood): leanne.maynard@completechildcare.co.uk
- **Any nursery manager email**: Requestor role

### Test Scenarios

1. **Route A (Simple)**: Submit request with cost £400, labour 3 days
2. **Route B (Standard)**: Submit request with cost £1,200, labour 8 days
3. **Route C (Complex)**: Submit request with cost £5,000, labour 15 days
4. **Revision Workflow**: Request revision, edit, resubmit
5. **Dashboard Visibility**: Verify all approvers see all requests

## Next Steps

### Short-term (2 weeks)
- Migrate localStorage to SharePoint Graph API
- Implement email notifications (Outlook)
- Create user guide

### Medium-term (4 weeks)
- Auto-escalation scheduled task (Azure Functions)
- File upload to SharePoint
- Production user testing

### Long-term
- Analytics dashboard
- Integration with facilities management system
- Mobile app

## Support

For issues or feedback, contact Alec Hodson (alec.hodson@completechildcare.co.uk)

---

**Version**: 1.0.0 (MVP)  
**Last Updated**: 2026-10-09  
**Status**: Ready for Testing
