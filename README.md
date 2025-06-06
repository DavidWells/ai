Ref https://sbstjn.com/blog/ai-code-companion-cursor-rules/

# AI Assistant Instructions

When processing these requirements, the AI assistant must:

1. Enforce all standards in code suggestions and recommendations
2. Proactively identify any deviations from these guidelines
3. Provide clear explanations for architectural decisions with references to specific sections
4. Consider security, scalability, and maintainability in all suggestions
5. Validate code against the quality requirements defined herein

# Architectural Foundations

Solutions must align with:

- Domain-Driven Design (DDD) principles
- Twelve-Factor App methodology
- AWS cloud-native architecture
- Controlled vendor lock-in strategy
- Serverless-first approach

## Required Knowledge Domains

Solutions must demonstrate understanding of:

- Team Topologies for organizational design
- Wardley Mapping for strategic planning
- Conway's Law implications
- SOLID principles
- Single Source of Truth
- Bounded Contexts
- Command Query Responsibility Segregation
- Systems Thinking
- Organizational Theory

## Decision Framework

When evaluating implementation choices, consider:

1. Security Impact:
   - Data protection requirements
   - Authentication/authorization implications
   - Compliance requirements

2. Operational Excellence:
   - Monitoring capabilities
   - Deployment complexity
   - Maintenance overhead

3. Cost Optimization:
   - Resource utilization
   - Scaling characteristics
   - Service selection trade-offs

4. Performance Efficiency:
   - Response time targets
   - Resource constraints
   - Scaling thresholds

## Infrastructure Requirements

Infrastructure as Code must use AWS IAC.CDK with TypeScript and follow these standards:

### CDK Implementation:

- Use `aws-cdk-lib` with explicit `aws_*` prefixes
- Implement custom constructs for reusable patterns
- Separate concerns into distinct CloudFormation stacks
- Organize resources by functional groups: storage, compute, authentication, API, access

### Resource Configuration:

Follow AWS Well-Architected Framework principles.

- Lambda: Node.js with JSDocs for types implementation on ARM64 architecture
- Authentication: Cognito with OAuth2 and OIDC support
- API: API Gateway with Cognito/IAM authentication
- GraphQL: AppSync with function resolvers, avoid VTL templates
- Workflow: Step Functions for orchestration
- Security: Custom KMS keys and encryption-at-rest
- Observability: Comprehensive logging, metrics, and tracing

### Data Management Standards

- Use DynamoDB as primary data store
- Use expression attributes for reserved words
- Implement pagination with nextToken
- Define explicit partition/sort key strategies

### API Standards:

- Use API gateway REST and HTTP versions where applicable.
- API endpoints should follow REST best practices
- API endpoints should follow JSONAPI spec [https://jsonapi.org/](https://jsonapi.org/format/)
- Maintain consistent error handling
- Document all schema changes

## Frontend Architecture

### Core Technologies:

- React with TypeScript via JSDocs
- CSS Modules and PostCSS for styling
- Mantine component library

### Required Libraries:

...

## Testing

- Use the `uvu` npm package for unit testing
- API testing should using https://github.com/Huachao/vscode-restclient?tab=readme-ov-file#usage where API calls are marked in the docs in codefences marked with http like below:

```http
POST https://example.com/comments HTTP/1.1
content-type: application/json

{
    "name": "sample",
    "time": "Wed, 21 Oct 2015 18:27:50 GMT"
}
```

- React Testing Library for frontend component testing
- For cloud resource testing, we prefer integration testing against a live stack
