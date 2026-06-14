# Docebo GraphQL Schema

## Overview

This is a conceptual GraphQL schema for the Docebo LMS (Learning Management System) platform. Docebo provides a REST API at https://developers.docebo.com/reference — this GraphQL schema models the same domain objects and relationships in GraphQL SDL form, enabling graph-style querying across the Docebo learning platform.

## Provider

- **Name**: Docebo
- **Type**: AI-powered Learning Management System (LMS)
- **REST API Docs**: https://developers.docebo.com/reference
- **Developer Portal**: https://developer.docebo.com
- **GitHub**: https://github.com/docebo
- **Base URL**: https://{domain}.docebosaas.com

## Schema Source

Derived from the Docebo REST API surface, which covers:

- Course and content management (courses, editions, catalogs, categories, channels, playlists)
- Learning plans and structured paths
- User management (users, profiles, branches, groups)
- Enrollment and progress tracking
- Assessments (tests, questions, answers, scores)
- Certifications and badges (gamification)
- Sessions and virtual/classroom instruction
- Reports and analytics
- Integrations (SCORM, xAPI/TinCan, AICC)
- Platform configuration (SSO, OAuth2, webhooks, API keys)
- Localization (languages, locales, custom fields)
- Skills and competency management

## Types Summary

| Category | Types |
|---|---|
| Courses & Content | Course, CourseEdition, CourseCatalog, Category, Channel, Playlist |
| Learning Paths | LearningPlan, LearningPlanItem |
| Enrollment & Progress | EnrolledUser, Enrollment, Completion, Progress |
| Sessions & Instruction | Session, SessionSchedule, Instructor, Classroom, VirtualClassroom, WebinarSession, Webinar |
| Assessments | Test, TestAttempt, Question, Answer, Score |
| Achievements | Certificate, Badge |
| Org Structure | Branch, Group, User, UserProfile, UserGroup, Subscription, Manager, SuperAdmin |
| Platform | Domain, Language, Locale, CustomField, AppConfig |
| Reporting | Report, ReportFilter, ReportExport, Widget, Dashboard, DashboardWidget |
| Integrations | Integration, SCORM, xAPI, TinCan, AICC |
| Security & Auth | AuthToken, OAuth2, WebhookEvent, Webhook, SSOConfig, SAMLConfig, APIKey |
| Skills | Skill, SkillLevel, CompetencyPath |

## Query Examples

### Fetch a Course with Enrolled Users

```graphql
query GetCourseWithEnrollments($courseId: ID!) {
  course(id: $courseId) {
    id
    name
    code
    type
    status
    category {
      id
      name
    }
    enrolledUsers {
      id
      user {
        id
        username
        email
      }
      enrollmentDate
      completionDate
      progress {
        percentage
        status
      }
    }
  }
}
```

### Fetch Learning Plan Progress for a User

```graphql
query GetUserLearningPlanProgress($userId: ID!, $planId: ID!) {
  user(id: $userId) {
    id
    username
    learningPlanProgress(planId: $planId) {
      learningPlan {
        id
        name
      }
      items {
        id
        course {
          id
          name
        }
        completion {
          status
          completedAt
          score
        }
      }
    }
  }
}
```

### List Users in a Branch

```graphql
query GetBranchUsers($branchId: ID!, $page: Int, $pageSize: Int) {
  branch(id: $branchId) {
    id
    name
    users(page: $page, pageSize: $pageSize) {
      totalCount
      nodes {
        id
        username
        email
        profile {
          firstName
          lastName
          jobTitle
        }
        groups {
          id
          name
        }
      }
    }
  }
}
```

### Generate a Report

```graphql
mutation CreateReport($input: CreateReportInput!) {
  createReport(input: $input) {
    report {
      id
      name
      type
      filters {
        field
        operator
        value
      }
    }
  }
}

query ExportReport($reportId: ID!, $format: ExportFormat!) {
  reportExport(reportId: $reportId, format: $format) {
    id
    status
    downloadUrl
    expiresAt
  }
}
```

## Mutation Examples

### Enroll a User in a Course

```graphql
mutation EnrollUser($input: EnrollUserInput!) {
  enrollUser(input: $input) {
    enrollment {
      id
      user {
        id
        username
      }
      course {
        id
        name
      }
      enrollmentDate
      status
    }
  }
}
```

### Award a Badge

```graphql
mutation AwardBadge($userId: ID!, $badgeId: ID!) {
  awardBadge(userId: $userId, badgeId: $badgeId) {
    badge {
      id
      name
      imageUrl
    }
    awardedAt
    user {
      id
      username
    }
  }
}
```

## Notes

- This is a conceptual schema. Docebo does not currently expose a native GraphQL endpoint.
- All type definitions map to resources documented in the Docebo REST API reference at https://developers.docebo.com/reference.
- Authentication follows OAuth2 client credentials or authorization code flows as described at https://developer.docebo.com/docs/api-guides.
- Rate limits apply per the Docebo platform tier; see rate-limits/docebo-rate-limits.yml.
