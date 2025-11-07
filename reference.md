# Reference
## Actions
<details><summary><code>client.Actions.Search(request) -> *mavenagigo.ActionsResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ActionsSearchRequest{}
client.Actions.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ActionsSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Actions.CreateOrUpdate(request) -> *mavenagigo.ActionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update an action or create it if it doesn't exist
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ActionRequest{
        ActionId: &mavenagigo.EntityIdBase{
            ReferenceId: "get-balance",
        },
        Name: "Get the user's balance",
        Description: "This action calls an API to get the user's current balance.",
        UserInteractionRequired: false,
        UserFormParameters: []*mavenagigo.ActionParameter{},
        Precondition: &mavenagigo.Precondition{
            Group: &mavenagigo.PreconditionGroup{
                Operator: mavenagigo.PreconditionGroupOperatorAnd,
                Preconditions: []*mavenagigo.Precondition{
                    &mavenagigo.Precondition{
                        User: &mavenagigo.MetadataPrecondition{
                            Key: "userKey",
                        },
                    },
                    &mavenagigo.Precondition{
                        User: &mavenagigo.MetadataPrecondition{
                            Key: "userKey2",
                        },
                    },
                },
            },
        },
        Language: mavenagigo.String(
            "en",
        ),
    }
client.Actions.CreateOrUpdate(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ActionRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Actions.Get(ActionReferenceId) -> *mavenagigo.ActionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an action by its supplied ID
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ActionGetRequest{}
client.Actions.Get(
        context.TODO(),
        "get-balance",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**actionReferenceId:** `string` — The reference ID of the action to get. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the action to get. If not provided the ID of the calling app will be used.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Actions.Patch(ActionReferenceId, request) -> *mavenagigo.ActionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update mutable action fields

The `appId` field can be provided to update an action owned by a different app. 
All other fields will overwrite the existing value on the action only if provided.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ActionPatchRequest{
        Instructions: mavenagigo.String(
            "Use this action when the user asks about their account balance or remaining credits.",
        ),
        LlmInclusionStatus: mavenagigo.LlmInclusionStatusWhenRelevant.Ptr(),
        SegmentId: &mavenagigo.EntityId{
            ReferenceId: "premium-users",
            AppId: "my-billing-system",
            OrganizationId: "acme",
            AgentId: "support",
            Type: mavenagigo.EntityTypeSegment,
        },
    }
client.Actions.Patch(
        context.TODO(),
        "get-balance",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**actionReferenceId:** `string` — The reference ID of the action to patch.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the action to patch. If not provided the ID of the calling app will be used.
    
</dd>
</dl>

<dl>
<dd>

**instructions:** `*string` — The instructions given to the LLM when determining whether to execute the action.
    
</dd>
</dl>

<dl>
<dd>

**llmInclusionStatus:** `*mavenagigo.LlmInclusionStatus` — Determines whether the action is sent to the LLM as part of a conversation.
    
</dd>
</dl>

<dl>
<dd>

**segmentId:** `*mavenagigo.EntityId` 

The ID of the segment that must be matched for the action to be relevant to a conversation. 
A null value will remove the segment from the action, it will be available on all conversations.

Segments are replacing inline preconditions - an action may not have both an inline precondition and a segment.
Inline precondition support will be removed in a future release.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Actions.Delete(ActionReferenceId) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete an action
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Actions.Delete(
        context.TODO(),
        "get-balance",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**actionReferenceId:** `string` — The reference ID of the action to unregister. All other entity ID fields are inferred from the request.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Agents
<details><summary><code>client.Agents.Search(request) -> *mavenagigo.AgentsSearchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for agents across all organizations.

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.AgentsSearchRequest{}
client.Agents.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.AgentsSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Agents.List(OrganizationReferenceId) -> []*mavenagigo.Agent</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Lists all agents for an organization
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Agents.List(
        context.TODO(),
        "organizationReferenceId",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The ID of the organization.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Agents.Create(OrganizationReferenceId, AgentReferenceId, request) -> *mavenagigo.Agent</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a new agent

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.CreateAgentRequest{
        Name: "name",
        Environment: mavenagigo.AgentEnvironmentDemo,
    }
client.Agents.Create(
        context.TODO(),
        "organizationReferenceId",
        "agentReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The ID of the organization.
    
</dd>
</dl>

<dl>
<dd>

**agentReferenceId:** `string` — The ID of the agent.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.CreateAgentRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Agents.Get(OrganizationReferenceId, AgentReferenceId) -> *mavenagigo.Agent</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an agent
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Agents.Get(
        context.TODO(),
        "organizationReferenceId",
        "agentReferenceId",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The ID of the organization.
    
</dd>
</dl>

<dl>
<dd>

**agentReferenceId:** `string` — The ID of the agent.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Agents.Patch(OrganizationReferenceId, AgentReferenceId, request) -> *mavenagigo.Agent</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update mutable agent fields 
All fields will overwrite the existing value on the agent only if provided.

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.AgentPatchRequest{}
client.Agents.Patch(
        context.TODO(),
        "organizationReferenceId",
        "agentReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The ID of the organization.
    
</dd>
</dl>

<dl>
<dd>

**agentReferenceId:** `string` — The ID of the agent.
    
</dd>
</dl>

<dl>
<dd>

**name:** `*string` — The name of the agent.
    
</dd>
</dl>

<dl>
<dd>

**environment:** `*mavenagigo.AgentEnvironment` — The environment of the agent.
    
</dd>
</dl>

<dl>
<dd>

**defaultTimezone:** `*string` — The agent's default timezone. This is used when a timezone is not set on a conversation.
    
</dd>
</dl>

<dl>
<dd>

**enabledPiiCategories:** `[]*mavenagigo.PiiCategory` — The PII categories that are enabled for the agent.
    
</dd>
</dl>

<dl>
<dd>

**systemFallbackMessage:** `*string` — The system fallback message.
    
</dd>
</dl>

<dl>
<dd>

**persona:** `*mavenagigo.LlmPersona` — The overall persona of the agent.
    
</dd>
</dl>

<dl>
<dd>

**additionalPromptText:** `*string` — Additional text directly appended to the prompt.
    
</dd>
</dl>

<dl>
<dd>

**categoryGenerationPromptText:** `*string` — LLM prompt for category generation.
    
</dd>
</dl>

<dl>
<dd>

**contentSafetyViolationResponsePromptText:** `*string` — LLM prompt for generating a response when the user's question has been detected as unsafe.
    
</dd>
</dl>

<dl>
<dd>

**rejectQuestionsWithoutKnowledge:** `*bool` — Return the system fallback message on all questions that have no relevant knowledge bases or actions.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Agents.Delete(OrganizationReferenceId, AgentReferenceId) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete an agent.

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Agents.Delete(
        context.TODO(),
        "organizationReferenceId",
        "agentReferenceId",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The ID of the organization.
    
</dd>
</dl>

<dl>
<dd>

**agentReferenceId:** `string` — The ID of the agent.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Analytics
<details><summary><code>client.Analytics.GetConversationTable(request) -> *mavenagigo.ConversationTableResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves structured conversation data formatted as a table, allowing users to group, filter, and define specific metrics to display as columns.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationTableRequest{
        ConversationFilter: &mavenagigo.ConversationFilter{
            Languages: []string{
                "en",
                "es",
            },
        },
        TimeGrouping: mavenagigo.TimeIntervalDay.Ptr(),
        FieldGroupings: []*mavenagigo.ConversationGroupBy{
            &mavenagigo.ConversationGroupBy{
                Field: mavenagigo.ConversationFieldCategory,
            },
        },
        ColumnDefinitions: []*mavenagigo.ConversationColumnDefinition{
            &mavenagigo.ConversationColumnDefinition{
                Header: "count",
                Metric: &mavenagigo.ConversationMetric{
                    Count: &mavenagigo.ConversationCount{},
                },
            },
            &mavenagigo.ConversationColumnDefinition{
                Header: "avg_first_response_time",
                Metric: &mavenagigo.ConversationMetric{
                    Average: &mavenagigo.ConversationAverage{
                        TargetField: mavenagigo.NumericConversationFieldFirstResponseTime,
                    },
                },
            },
            &mavenagigo.ConversationColumnDefinition{
                Header: "percentile_handle_time",
                Metric: &mavenagigo.ConversationMetric{
                    Percentile: &mavenagigo.ConversationPercentile{
                        TargetField: mavenagigo.NumericConversationFieldHandleTime,
                        Percentile: 25,
                    },
                },
            },
        },
    }
client.Analytics.GetConversationTable(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ConversationTableRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Analytics.GetConversationChart(request) -> *mavenagigo.ChartResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Fetches conversation data visualized in a chart format. Supported chart types include pie chart, date histogram, and stacked bar charts.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationChartRequest{
        PieChart: &mavenagigo.ConversationPieChartRequest{
            ConversationFilter: &mavenagigo.ConversationFilter{
                Languages: []string{
                    "en",
                    "es",
                },
            },
            GroupBy: &mavenagigo.ConversationGroupBy{
                Field: mavenagigo.ConversationFieldCategory,
            },
            Metric: &mavenagigo.ConversationMetric{
                Count: &mavenagigo.ConversationCount{},
            },
        },
    }
client.Analytics.GetConversationChart(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ConversationChartRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Analytics.ExportConversationTable(request) -> string</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export the conversation analytics table to a CSV file.

This outputs the current table view defined by the request. For most programmatic use cases, prefer `getConversationTable` and format client-side. The CSV format may change and should not be relied upon by code consumers. A maximum of 10,000 rows can be exported at a time.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationTableRequest{
        FieldGroupings: []*mavenagigo.ConversationGroupBy{
            &mavenagigo.ConversationGroupBy{
                Field: mavenagigo.ConversationFieldCategory,
            },
            &mavenagigo.ConversationGroupBy{
                Field: mavenagigo.ConversationFieldCategory,
            },
        },
        ColumnDefinitions: []*mavenagigo.ConversationColumnDefinition{
            &mavenagigo.ConversationColumnDefinition{
                Metric: &mavenagigo.ConversationMetric{
                    Count: &mavenagigo.ConversationCount{},
                },
                Header: "header",
            },
            &mavenagigo.ConversationColumnDefinition{
                Metric: &mavenagigo.ConversationMetric{
                    Count: &mavenagigo.ConversationCount{},
                },
                Header: "header",
            },
        },
    }
client.Analytics.ExportConversationTable(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ConversationTableRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Analytics.GetFeedbackTable(request) -> *mavenagigo.FeedbackTableResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves structured feedback data formatted as a table, allowing users to group, filter,  and define specific metrics to display as columns.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.FeedbackTableRequest{
        FeedbackFilter: &mavenagigo.FeedbackFilter{
            Types: []mavenagigo.FeedbackType{
                mavenagigo.FeedbackTypeThumbsUp,
                mavenagigo.FeedbackTypeInsert,
            },
        },
        FieldGroupings: []*mavenagigo.FeedbackGroupBy{
            &mavenagigo.FeedbackGroupBy{
                Field: mavenagigo.FeedbackFieldCreatedBy,
            },
        },
        ColumnDefinitions: []*mavenagigo.FeedbackColumnDefinition{
            &mavenagigo.FeedbackColumnDefinition{
                Header: "feedback_count",
                Metric: &mavenagigo.FeedbackMetric{
                    Count: &mavenagigo.FeedbackCount{},
                },
            },
        },
    }
client.Analytics.GetFeedbackTable(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.FeedbackTableRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Analytics.GetAgentUserTable(request) -> *mavenagigo.AgentUserTableResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves structured agent user data formatted as a table, allowing users to group, filter,  and define specific metrics to display as columns.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.AgentUserTableRequest{
        AgentUserFilter: &mavenagigo.AgentUserFilter{
            Search: mavenagigo.String(
                "john",
            ),
        },
        ColumnDefinitions: []*mavenagigo.AgentUserColumnDefinition{
            &mavenagigo.AgentUserColumnDefinition{
                Header: "user_count",
                Metric: &mavenagigo.AgentUserMetric{
                    Count: &mavenagigo.AgentUserCount{},
                },
            },
        },
    }
client.Analytics.GetAgentUserTable(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.AgentUserTableRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## AppSettings
<details><summary><code>client.AppSettings.Search() -> *mavenagigo.SearchAppSettingsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search for app settings which have the `$index` key set to the provided value.

You can set the `$index` key using the Update app settings API.

<Warning>This API currently requires an organization ID and agent ID for any agent which is installed on the app. This requirement will be removed in a future update.</Warning>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.SearchAppSettingsRequest{
        Index: "index",
    }
client.AppSettings.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**index:** `string` — Will return all settings which have the `$index` key set to the provided value.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.AppSettings.Get() -> map[string]any</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get app settings set during installation
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.AppSettings.Get(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.AppSettings.Update(request) -> map[string]any</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update app settings. Performs a merge of the provided settings with the existing app settings.

- If a new key is provided, it will be added to the app settings.
- If an existing key is provided, it will be updated.
- No keys will be removed.

Note that if an array value is provided it will fully replace an existing value as arrays cannot be merged.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := map[string]any{
        "string": map[string]any{
            "key": "value",
        },
    }
client.AppSettings.Update(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `map[string]any` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Assets
<details><summary><code>client.Assets.InitiateUpload(request) -> *mavenagigo.InitiateAssetUploadResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Initiate an upload. 
Returns a pre-signed URL for direct file upload and an asset ID for subsequent operations.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.InitiateAssetUploadRequest{
        Type: "type",
    }
client.Assets.InitiateUpload(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.InitiateAssetUploadRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Assets.CommitUpload(AssetReferenceId, request) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Commit an upload after successful file transfer.
Updates the asset status and makes it available for use.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.CommitAssetUploadRequest{}
client.Assets.CommitUpload(
        context.TODO(),
        "assetReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**assetReferenceId:** `string` — The reference ID of the asset to commit (provided by the initiate call). All other entity ID fields are inferred from the API request.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.CommitAssetUploadRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Conversation
<details><summary><code>client.Conversation.Initialize(request) -> *mavenagigo.ConversationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Initialize a new conversation. 
Only required if the ask request wishes to supply conversation level data or when syncing to external systems.

Conversations can not be modified using this API. If the conversation already exists then the existing conversation will be returned.

After initialization,
- metadata can be changed using the `updateConversationMetadata` API.
- messages can be added to the conversation with the `appendNewMessages` or `ask` APIs.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationRequest{
        ConversationId: &mavenagigo.EntityIdBase{
            ReferenceId: "referenceId",
        },
        Messages: []*mavenagigo.ConversationMessageRequest{
            &mavenagigo.ConversationMessageRequest{
                ConversationMessageId: &mavenagigo.EntityIdBase{
                    ReferenceId: "referenceId",
                },
                UserId: &mavenagigo.EntityIdBase{
                    ReferenceId: "referenceId",
                },
                Text: "text",
                UserMessageType: mavenagigo.UserConversationMessageTypeUser,
            },
            &mavenagigo.ConversationMessageRequest{
                ConversationMessageId: &mavenagigo.EntityIdBase{
                    ReferenceId: "referenceId",
                },
                UserId: &mavenagigo.EntityIdBase{
                    ReferenceId: "referenceId",
                },
                Text: "text",
                UserMessageType: mavenagigo.UserConversationMessageTypeUser,
            },
        },
    }
client.Conversation.Initialize(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ConversationRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.Patch(ConversationId, request) -> *mavenagigo.ConversationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update mutable conversation fields. 

The `appId` field can be provided to update a conversation owned by a different app. 
All other fields will overwrite the existing value on the conversation only if provided.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationPatchRequest{
        LlmEnabled: mavenagigo.Bool(
            true,
        ),
    }
client.Conversation.Patch(
        context.TODO(),
        "conversation-0",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of the conversation to patch
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.ConversationPatchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.Get(ConversationId) -> *mavenagigo.ConversationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a conversation
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationGetRequest{}
client.Conversation.Get(
        context.TODO(),
        "conversationId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of the conversation to get
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the conversation to get. If not provided the ID of the calling app will be used.
    
</dd>
</dl>

<dl>
<dd>

**translationLanguage:** `*string` — The language to translate the conversation analysis into
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.Delete(ConversationId) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Wipes a conversation of all user data. 
The conversation ID will still exist and non-user specific data will still be retained. 
Attempts to modify or add messages to the conversation will throw an error. 

Simulation conversations will no longer be visible in search results nor metrics. 
Non-simulation conversations will remain visible - they can not be fully removed from the system.

<Warning>This is a destructive operation and cannot be undone. <br/><br/>
The exact fields cleared include: the conversation subject, userRequest, agentResponse. 
As well as the text response, followup questions, and backend LLM prompt of all messages.</Warning>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationDeleteRequest{
        Reason: "GDPR deletion request 1234.",
    }
client.Conversation.Delete(
        context.TODO(),
        "conversation-0",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of the conversation to delete
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the conversation to delete. If not provided the ID of the calling app will be used.
    
</dd>
</dl>

<dl>
<dd>

**reason:** `string` — The reason for deleting the conversation. This message will replace all user messages in the conversation.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.AppendNewMessages(ConversationId, request) -> *mavenagigo.ConversationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Append messages to an existing conversation. The conversation must be initialized first. If a message with the same ID already exists, it will be ignored. Messages do not allow modification.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := []*mavenagigo.ConversationMessageRequest{
        &mavenagigo.ConversationMessageRequest{
            ConversationMessageId: &mavenagigo.EntityIdBase{
                ReferenceId: "referenceId",
            },
            UserId: &mavenagigo.EntityIdBase{
                ReferenceId: "referenceId",
            },
            Text: "text",
            UserMessageType: mavenagigo.UserConversationMessageTypeUser,
        },
        &mavenagigo.ConversationMessageRequest{
            ConversationMessageId: &mavenagigo.EntityIdBase{
                ReferenceId: "referenceId",
            },
            UserId: &mavenagigo.EntityIdBase{
                ReferenceId: "referenceId",
            },
            Text: "text",
            UserMessageType: mavenagigo.UserConversationMessageTypeUser,
        },
    }
client.Conversation.AppendNewMessages(
        context.TODO(),
        "conversationId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of the conversation to append messages to
    
</dd>
</dl>

<dl>
<dd>

**request:** `[]*mavenagigo.ConversationMessageRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.Ask(ConversationId, request) -> *mavenagigo.ConversationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an answer from Maven for a given user question. If the user question or its answer already exists, 
they will be reused and will not be updated. Messages do not allow modification once generated. 

Concurrency Behavior:
- If another API call is made for the same user question while a response is mid-stream, partial answers may be returned.
- The second caller will receive a truncated or partial response depending on where the first stream is in its processing. The first caller's stream will remain unaffected and continue delivering the full response.

Known Limitation:
- The API does not currently expose metadata indicating whether a response or message is incomplete. This will be addressed in a future update.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.AskRequest{
        ConversationMessageId: &mavenagigo.EntityIdBase{
            ReferenceId: "message-0",
        },
        UserId: &mavenagigo.EntityIdBase{
            ReferenceId: "user-0",
        },
        Text: "How do I reset my password?",
        Attachments: []*mavenagigo.AttachmentRequest{
            &mavenagigo.AttachmentRequest{
                Type: "image/png",
                Content: []byte("iVBORw0KGgo..."),
            },
        },
        TransientData: map[string]string{
            "userToken": "abcdef123",
            "queryApiKey": "foobar456",
        },
        Timezone: mavenagigo.String(
            "America/New_York",
        ),
    }
client.Conversation.Ask(
        context.TODO(),
        "conversation-0",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of a new or existing conversation to use as context for the question
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.AskRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.AskStream(ConversationId, request) -> mavenagigo.StreamResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an answer from Maven for a given user question with a streaming response. The response will be sent as a stream of events. 
The text portions of stream responses should be concatenated to form the full response text. 
Action and metadata events should overwrite past data and do not need concatenation.

If the user question or its answer already exists, they will be reused and will not be updated. 
Messages do not allow modification once generated.
        
Concurrency Behavior:
- If another API call is made for the same user question while a response is mid-stream, partial answers may be returned.
- The second caller will receive a truncated or partial response depending on where the first stream is in its processing. The first caller's stream will remain unaffected and continue delivering the full response.

Known Limitation:
- The API does not currently expose metadata indicating whether a response or message is incomplete. This will be addressed in a future update.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.AskRequest{
        ConversationMessageId: &mavenagigo.EntityIdBase{
            ReferenceId: "message-0",
        },
        UserId: &mavenagigo.EntityIdBase{
            ReferenceId: "user-0",
        },
        Text: "How do I reset my password?",
        Attachments: []*mavenagigo.AttachmentRequest{
            &mavenagigo.AttachmentRequest{
                Type: "image/png",
                Content: []byte("iVBORw0KGgo..."),
            },
        },
        TransientData: map[string]string{
            "userToken": "abcdef123",
            "queryApiKey": "foobar456",
        },
        Timezone: mavenagigo.String(
            "America/New_York",
        ),
    }
client.Conversation.AskStream(
        context.TODO(),
        "conversation-0",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of a new or existing conversation to use as context for the question
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.AskRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.AskObjectStream(ConversationId, request) -> mavenagigo.ObjectStreamResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Generate a structured object response based on a provided schema and user prompt with a streaming response. 
The response will be sent as a stream of events containing text, start, and end events.
The text portions of stream responses should be concatenated to form the full response text.

If the user question and object response already exist, they will be reused and not updated.

Concurrency Behavior:
- If another API call is made for the same user question while a response is mid-stream, partial answers may be returned.
- The second caller will receive a truncated or partial response depending on where the first stream is in its processing. The first caller's stream will remain unaffected and continue delivering the full response.

Known Limitations:
- Schema enforcement is best-effort and may not guarantee exact conformity.
- The API does not currently expose metadata indicating whether a response or message is incomplete. This will be addressed in a future update.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.AskObjectRequest{
        Schema: "schema",
        ConversationMessageId: &mavenagigo.EntityIdBase{
            ReferenceId: "referenceId",
        },
        UserId: &mavenagigo.EntityIdBase{
            ReferenceId: "referenceId",
        },
        Text: "text",
    }
client.Conversation.AskObjectStream(
        context.TODO(),
        "conversationId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of a new or existing conversation to use as context for the object generation request
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.AskObjectRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.Categorize(ConversationId) -> *mavenagigo.CategorizationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Uses an LLM flow to categorize the conversation. Experimental.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Conversation.Categorize(
        context.TODO(),
        "conversationId",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of the conversation to categorize
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.CreateFeedback(request) -> *mavenagigo.Feedback</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update feedback or create it if it doesn't exist
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.FeedbackRequest{
        FeedbackId: &mavenagigo.EntityIdBase{
            ReferenceId: "feedback-0",
        },
        UserId: &mavenagigo.EntityIdBase{
            ReferenceId: "user-0",
        },
        ConversationId: &mavenagigo.EntityIdBase{
            ReferenceId: "conversation-0",
        },
        ConversationMessageId: &mavenagigo.EntityIdBase{
            ReferenceId: "message-1",
        },
        Type: mavenagigo.FeedbackTypeThumbsUp,
        Text: mavenagigo.String(
            "Great answer!",
        ),
    }
client.Conversation.CreateFeedback(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.FeedbackRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.SubmitActionForm(ConversationId, request) -> *mavenagigo.ConversationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Submit a filled out action form. 
Action forms can not be submitted more than once, attempting to do so will result in an error.

Additionally, form submission is only allowed when the form is the last message in the conversation. 
Forms should be disabled in surface UI if a conversation continues and they remain unsubmitted.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.SubmitActionFormRequest{
        ActionFormId: "actionFormId",
        Parameters: map[string]*mavenagigo.ActionFormRequestParamValue{
            "parameters": &mavenagigo.ActionFormRequestParamValue{
                Unknown: map[string]any{
                    "key": "value",
                },
            },
        },
    }
client.Conversation.SubmitActionForm(
        context.TODO(),
        "conversationId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of a conversation the form being submitted belongs to
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.SubmitActionFormRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.AddConversationMetadata(ConversationId, request) -> map[string]string</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Replaced by `updateConversationMetadata`. 

Adds metadata to an existing conversation. If a metadata field already exists, it will be overwritten.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := map[string]string{
        "string": "string",
    }
client.Conversation.AddConversationMetadata(
        context.TODO(),
        "conversationId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of a conversation the metadata being added belongs to
    
</dd>
</dl>

<dl>
<dd>

**request:** `map[string]string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.UpdateConversationMetadata(ConversationId, request) -> *mavenagigo.ConversationMetadata</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update metadata supplied by the calling application for an existing conversation. 
Does not modify metadata saved by other apps.

If a metadata field already exists for the calling app, it will be overwritten. 
If it does not exist, it will be added. Will not remove metadata fields.

Returns all metadata saved by any app on the conversation.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.UpdateMetadataRequest{
        AppId: mavenagigo.String(
            "conversation-owning-app",
        ),
        Values: map[string]string{
            "key": "newValue",
        },
    }
client.Conversation.UpdateConversationMetadata(
        context.TODO(),
        "conversation-0",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**conversationId:** `string` — The ID of the conversation to modify metadata for
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.UpdateMetadataRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.Search(request) -> *mavenagigo.ConversationsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search conversations
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationsSearchRequest{}
client.Conversation.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ConversationsSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.Export(request) -> string</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export conversations to a CSV file. 

This will output a summary of each conversation that matches the supplied filter. A maximum of 10,000 conversations can be exported at a time.

For most use cases it is recommended to use the `search` API instead and convert the JSON response to your desired format. 
The CSV format may change over time and should not be relied upon by code consumers.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationsSearchRequest{}
client.Conversation.Export(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ConversationsSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Conversation.DeliverMessage(request) -> *mavenagigo.DeliverMessageResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deliver a message to a user or conversation.

<Warning>
Currently, messages can only be successfully delivered to conversations with the `ASYNC` capability that are `open`. 
User message delivery is not yet supported.
</Warning>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.DeliverMessageRequest{
        User: &mavenagigo.DeliverUserMessageRequest{
            UserId: &mavenagigo.EntityIdWithoutAgent{
                Type: mavenagigo.EntityTypeAgent,
                AppId: "appId",
                ReferenceId: "referenceId",
            },
            Message: &mavenagigo.ConversationMessageRequest{
                ConversationMessageId: &mavenagigo.EntityIdBase{
                    ReferenceId: "referenceId",
                },
                UserId: &mavenagigo.EntityIdBase{
                    ReferenceId: "referenceId",
                },
                Text: "text",
                UserMessageType: mavenagigo.UserConversationMessageTypeUser,
            },
        },
    }
client.Conversation.DeliverMessage(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.DeliverMessageRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Events
<details><summary><code>client.Events.Create(request) -> *mavenagigo.EventResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a new event
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.EventRequest{
        UserEvent: &mavenagigo.NovelUserEvent{
            Id: &mavenagigo.EntityIdBase{
                ReferenceId: "referenceId",
            },
            EventName: mavenagigo.UserEventNameButtonClicked,
            UserInfo: &mavenagigo.EventUserInfoBase{
                Id: &mavenagigo.EntityIdBase{
                    ReferenceId: "referenceId",
                },
            },
        },
    }
client.Events.Create(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.EventRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Events.Search(request) -> *mavenagigo.EventsSearchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search events
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.EventsSearchRequest{}
client.Events.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.EventsSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Events.Get(EventId) -> *mavenagigo.EventResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve details of a specific Event item by its ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.EventGetRequest{
        AppId: "appId",
    }
client.Events.Get(
        context.TODO(),
        "eventId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**eventId:** `string` — The ID of the Event to get.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `string` — The App ID of the Event to retrieve
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Events.Export(request) -> string</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Export events to a CSV file.

This will output a summary of each event that matches the supplied filter. A maximum of 10,000 events can be exported at a time. For most use cases it is recommended to use the search API instead and convert the JSON response to your desired format. The CSV format may change over time and should not be relied upon by code consumers.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.EventsSearchRequest{}
client.Events.Export(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.EventsSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Inbox
<details><summary><code>client.Inbox.Search(request) -> *mavenagigo.InboxSearchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a paginated list of inbox items for an agent.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.InboxSearchRequest{}
client.Inbox.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.InboxSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Inbox.Get(InboxItemId) -> *mavenagigo.InboxItem</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve details of a specific inbox item by its ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.InboxItemRequest{
        AppId: "appId",
    }
client.Inbox.Get(
        context.TODO(),
        "inboxItemId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**inboxItemId:** `string` — The ID of the inbox item to get. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `string` — The App ID of the inbox item to retrieve
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Inbox.GetFix(InboxItemFixId) -> *mavenagigo.InboxItemFix</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a suggested fix. Includes document information if the fix is a Missing Knowledge suggestion.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.InboxItemFixRequest{
        AppId: "appId",
    }
client.Inbox.GetFix(
        context.TODO(),
        "inboxItemFixId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**inboxItemFixId:** `string` — Unique identifier for the inbox fix.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `string` — The App ID of the inbox item fix to retrieve
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Inbox.ApplyFixes(InboxItemId, request) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Apply a list of fixes belonging to an inbox item.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ApplyFixesRequest{
        AppId: "appId",
        FixReferenceIds: []string{
            "fixReferenceIds",
            "fixReferenceIds",
        },
    }
client.Inbox.ApplyFixes(
        context.TODO(),
        "inboxItemId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**inboxItemId:** `string` — Unique identifier for the inbox item.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.ApplyFixesRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Inbox.Ignore(InboxItemId) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Ignore a specific inbox item by its ID.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.InboxItemIgnoreRequest{
        AppId: "appId",
    }
client.Inbox.Ignore(
        context.TODO(),
        "inboxItemId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**inboxItemId:** `string` — Unique identifier for the inbox item.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `string` — The App ID of the inbox item fix to ignore
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Knowledge
<details><summary><code>client.Knowledge.SearchKnowledgeBases(request) -> *mavenagigo.KnowledgeBasesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search knowledge bases
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeBaseSearchRequest{}
client.Knowledge.SearchKnowledgeBases(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.KnowledgeBaseSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.CreateOrUpdateKnowledgeBase(request) -> *mavenagigo.KnowledgeBaseResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update a knowledge base or create it if it doesn't exist.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeBaseRequest{
        KnowledgeBaseId: &mavenagigo.EntityIdBase{
            ReferenceId: "help-center",
        },
        Name: "Help center",
    }
client.Knowledge.CreateOrUpdateKnowledgeBase(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.KnowledgeBaseRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.GetKnowledgeBase(KnowledgeBaseReferenceId) -> *mavenagigo.KnowledgeBaseResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an existing knowledge base by its supplied ID
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeBaseGetRequest{}
client.Knowledge.GetKnowledgeBase(
        context.TODO(),
        "help-center",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base to get. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the knowledge base to get. If not provided the ID of the calling app will be used.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.RefreshKnowledgeBase(KnowledgeBaseReferenceId, request) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Request that a knowledge base refresh itself.

Knowledge bases refresh on a schedule determined by the `refreshFrequency` field.
They can also be refreshed on demand by calling this endpoint.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeBaseRefreshRequest{
        AppId: mavenagigo.String(
            "readme",
        ),
    }
client.Knowledge.RefreshKnowledgeBase(
        context.TODO(),
        "help-center",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base to refresh. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.KnowledgeBaseRefreshRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.PatchKnowledgeBase(KnowledgeBaseReferenceId, request) -> *mavenagigo.KnowledgeBaseResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update mutable knowledge base fields

The `appId` field can be provided to update a knowledge base owned by a different app. 
All other fields will overwrite the existing value on the knowledge base only if provided.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeBasePatchRequest{
        Name: mavenagigo.String(
            "Updated Help Center",
        ),
        Tags: []string{
            "tag1",
            "tag2",
            "tag3",
        },
        SegmentId: &mavenagigo.EntityId{
            ReferenceId: "premium-users",
            AppId: "readme",
            OrganizationId: "acme",
            AgentId: "support",
            Type: mavenagigo.EntityTypeSegment,
        },
    }
client.Knowledge.PatchKnowledgeBase(
        context.TODO(),
        "help-center",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base to patch.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the knowledge base to patch. If not provided the ID of the calling app will be used.
    
</dd>
</dl>

<dl>
<dd>

**name:** `*string` — The name of the knowledge base.
    
</dd>
</dl>

<dl>
<dd>

**tags:** `[]string` — The tags of the knowledge base.
    
</dd>
</dl>

<dl>
<dd>

**llmInclusionStatus:** `*mavenagigo.LlmInclusionStatus` — Determines whether documents in the knowledge base are sent to the LLM as part of a conversation. Note that at this time knowledge bases can not be set to `ALWAYS`.
    
</dd>
</dl>

<dl>
<dd>

**precondition:** `*mavenagigo.Precondition` — The preconditions that must be met for a knowledge base to be relevant to a conversation. Can be used to restrict knowledge bases to certain types of users. A null value will remove the precondition from the knowledge base, it will be available on all conversations.
    
</dd>
</dl>

<dl>
<dd>

**segmentId:** `*mavenagigo.EntityId` 

The ID of the segment that must be matched for the knowledge base to be relevant to a conversation. 
A null value will remove the segment from the knowledge base, it will be available on all conversations.

Segments are replacing inline preconditions - a knowledge base may not have both an inline precondition and a segment.
Inline precondition support will be removed in a future release.
    
</dd>
</dl>

<dl>
<dd>

**refreshFrequency:** `*mavenagigo.KnowledgeBaseRefreshFrequency` — How often the knowledge base should be refreshed.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.CreateKnowledgeBaseVersion(KnowledgeBaseReferenceId, request) -> *mavenagigo.KnowledgeBaseVersion</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a new knowledge base version.

If an existing version is in progress, then that version will be finalized in an error state.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeBaseVersionRequest{
        Type: mavenagigo.KnowledgeBaseVersionTypeFull,
    }
client.Knowledge.CreateKnowledgeBaseVersion(
        context.TODO(),
        "help-center",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base to create a version for. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.KnowledgeBaseVersionRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.FinalizeKnowledgeBaseVersion(KnowledgeBaseReferenceId, request) -> *mavenagigo.KnowledgeBaseVersion</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Finalize the latest knowledge base version. Required to indicate the version is complete. Will throw an exception if the latest version is not in progress.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.FinalizeKnowledgeBaseVersionRequest{
        VersionId: &mavenagigo.EntityIdWithoutAgent{
            Type: mavenagigo.EntityTypeKnowledgeBaseVersion,
            ReferenceId: "versionId",
            AppId: "maven",
        },
        Status: mavenagigo.KnowledgeBaseVersionFinalizeStatusSucceeded.Ptr(),
    }
client.Knowledge.FinalizeKnowledgeBaseVersion(
        context.TODO(),
        "help-center",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base to finalize a version for. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.FinalizeKnowledgeBaseVersionRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.ListKnowledgeBaseVersions(KnowledgeBaseReferenceId) -> *mavenagigo.KnowledgeBaseVersionsListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List all active versions for a knowledge base. Returns the most recent versions first.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeBaseVersionsListRequest{}
client.Knowledge.ListKnowledgeBaseVersions(
        context.TODO(),
        "knowledgeBaseReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base to list versions for. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the knowledge base. If not provided the ID of the calling app will be used.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.SearchKnowledgeDocuments(request) -> *mavenagigo.KnowledgeDocumentsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search knowledge documents
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeDocumentSearchRequest{}
client.Knowledge.SearchKnowledgeDocuments(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.KnowledgeDocumentSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.CreateKnowledgeDocument(KnowledgeBaseReferenceId, request) -> *mavenagigo.KnowledgeDocumentResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create or update a knowledge document. Requires an existing knowledge base with an in progress version. 
Will throw an exception if the latest version is not in progress.
        
<Tip>
This API maintains document version history. If for the same reference ID none of the `title`, `text`, `sourceUrl`, `metadata` fields 
have changed, a new document version will not be created. The existing version will be reused.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeDocumentRequest{
        KnowledgeDocumentId: &mavenagigo.EntityIdBase{
            ReferenceId: "getting-started",
        },
        VersionId: &mavenagigo.EntityIdWithoutAgent{
            Type: mavenagigo.EntityTypeKnowledgeBaseVersion,
            ReferenceId: "versionId",
            AppId: "maven",
        },
        ContentType: mavenagigo.KnowledgeDocumentContentTypeMarkdown,
        Content: "## Getting started\nThis is a getting started guide for the help center.",
        Title: "Getting started",
        Metadata: map[string]string{
            "category": "getting-started",
        },
    }
client.Knowledge.CreateKnowledgeDocument(
        context.TODO(),
        "help-center",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base to create a document for. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.KnowledgeDocumentRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.DeleteKnowledgeDocument(KnowledgeBaseReferenceId, KnowledgeDocumentReferenceId, request) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete knowledge document from a specific version. 
Requires an existing knowledge base with an in progress version of type PARTIAL. Will throw an exception if the version is not in progress.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeDeleteRequest{
        VersionId: &mavenagigo.EntityIdWithoutAgent{
            Type: mavenagigo.EntityTypeKnowledgeBaseVersion,
            AppId: "maven",
            ReferenceId: "versionId",
        },
    }
client.Knowledge.DeleteKnowledgeDocument(
        context.TODO(),
        "help-center",
        "getting-started",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base that contains the document to delete. All other entity ID fields are inferred from the request
    
</dd>
</dl>

<dl>
<dd>

**knowledgeDocumentReferenceId:** `string` — The reference ID of the knowledge document to delete. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.KnowledgeDeleteRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.GetKnowledgeDocument(KnowledgeBaseVersionReferenceId, KnowledgeDocumentReferenceId) -> *mavenagigo.KnowledgeDocumentResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a knowledge document by its supplied version and document IDs. Response includes document content in markdown format.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeDocumentGetRequest{
        KnowledgeBaseVersionAppId: "knowledgeBaseVersionAppId",
    }
client.Knowledge.GetKnowledgeDocument(
        context.TODO(),
        "knowledgeBaseVersionReferenceId",
        "knowledgeDocumentReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseVersionReferenceId:** `string` — The reference ID of the knowledge base version that contains the document. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**knowledgeDocumentReferenceId:** `string` — The reference ID of the knowledge document to get. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**knowledgeBaseVersionAppId:** `string` — The App ID of the knowledge base version.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Knowledge.PatchKnowledgeDocument(KnowledgeBaseReferenceId, KnowledgeDocumentReferenceId, request) -> *mavenagigo.KnowledgeDocumentResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update mutable knowledge document fields that can be set independently of a knowledge base version.

For any changes in document content see the `createKnowledgeBaseVersion` and `createKnowledgeDocument` endpoints.

The `knowledgeBaseAppId` field can be provided to update a knowledge document in a knowledge base owned by a different app. 
All other fields will overwrite the existing value on the knowledge document only if provided.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.KnowledgeDocumentPatchRequest{
        LlmInclusionStatus: mavenagigo.LlmInclusionStatusAlways.Ptr(),
    }
client.Knowledge.PatchKnowledgeDocument(
        context.TODO(),
        "help-center",
        "how-it-works",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**knowledgeBaseReferenceId:** `string` — The reference ID of the knowledge base to patch.
    
</dd>
</dl>

<dl>
<dd>

**knowledgeDocumentReferenceId:** `string` — The reference ID of the knowledge document to patch.
    
</dd>
</dl>

<dl>
<dd>

**knowledgeBaseAppId:** `*string` — The App ID of the knowledge base that contains the knowledge document to patch. If not provided the ID of the calling app will be used.
    
</dd>
</dl>

<dl>
<dd>

**llmInclusionStatus:** `*mavenagigo.LlmInclusionStatus` — Determines whether this document is sent to the LLM as part of a conversation.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Organizations
<details><summary><code>client.Organizations.Create(OrganizationReferenceId, request) -> *mavenagigo.Organization</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a new organization.

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.CreateOrganizationRequest{
        Name: "name",
        DefaultLanguage: "defaultLanguage",
    }
client.Organizations.Create(
        context.TODO(),
        "organizationReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The reference ID of the organization.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.CreateOrganizationRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organizations.Get(OrganizationReferenceId) -> *mavenagigo.Organization</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an organization by ID
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Organizations.Get(
        context.TODO(),
        "organizationReferenceId",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The reference ID of the organization.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organizations.Patch(OrganizationReferenceId, request) -> *mavenagigo.Organization</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update mutable organization fields.
All fields will overwrite the existing value on the organization only if provided.

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.OrganizationPatchRequest{}
client.Organizations.Patch(
        context.TODO(),
        "organizationReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The reference ID of the organization.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.OrganizationPatchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organizations.Delete(OrganizationReferenceId) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete an organization.

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Organizations.Delete(
        context.TODO(),
        "organizationReferenceId",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**organizationReferenceId:** `string` — The reference ID of the organization.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organizations.GetConversationTable(request) -> *mavenagigo.ConversationTableResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieves structured conversation data across all organizations, formatted as a table, 
allowing users to group, filter, and define specific metrics to display as columns.

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationTableRequest{
        ConversationFilter: &mavenagigo.ConversationFilter{
            Languages: []string{
                "en",
                "es",
            },
        },
        TimeGrouping: mavenagigo.TimeIntervalDay.Ptr(),
        FieldGroupings: []*mavenagigo.ConversationGroupBy{
            &mavenagigo.ConversationGroupBy{
                Field: mavenagigo.ConversationFieldCategory,
            },
        },
        ColumnDefinitions: []*mavenagigo.ConversationColumnDefinition{
            &mavenagigo.ConversationColumnDefinition{
                Header: "count",
                Metric: &mavenagigo.ConversationMetric{
                    Count: &mavenagigo.ConversationCount{},
                },
            },
            &mavenagigo.ConversationColumnDefinition{
                Header: "avg_first_response_time",
                Metric: &mavenagigo.ConversationMetric{
                    Average: &mavenagigo.ConversationAverage{
                        TargetField: mavenagigo.NumericConversationFieldFirstResponseTime,
                    },
                },
            },
            &mavenagigo.ConversationColumnDefinition{
                Header: "percentile_handle_time",
                Metric: &mavenagigo.ConversationMetric{
                    Percentile: &mavenagigo.ConversationPercentile{
                        TargetField: mavenagigo.NumericConversationFieldHandleTime,
                        Percentile: 25,
                    },
                },
            },
        },
    }
client.Organizations.GetConversationTable(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ConversationTableRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Organizations.GetConversationChart(request) -> *mavenagigo.ChartResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Fetches conversation data across all organizations, visualized in a chart format. 
Supported chart types include pie chart, date histogram, and stacked bar charts.

<Tip>
This endpoint requires additional permissions. Contact support to request access.
</Tip>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.ConversationChartRequest{
        PieChart: &mavenagigo.ConversationPieChartRequest{
            ConversationFilter: &mavenagigo.ConversationFilter{
                Languages: []string{
                    "en",
                    "es",
                },
            },
            GroupBy: &mavenagigo.ConversationGroupBy{
                Field: mavenagigo.ConversationFieldCategory,
            },
            Metric: &mavenagigo.ConversationMetric{
                Count: &mavenagigo.ConversationCount{},
            },
        },
    }
client.Organizations.GetConversationChart(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.ConversationChartRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Segments
<details><summary><code>client.Segments.Search(request) -> *mavenagigo.SegmentsSearchResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.SegmentsSearchRequest{}
client.Segments.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.SegmentsSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Segments.CreateOrUpdate(request) -> *mavenagigo.SegmentResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update a segment or create it if it doesn't exist.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.SegmentRequest{
        SegmentId: &mavenagigo.EntityIdBase{
            ReferenceId: "admin-users",
        },
        Name: "Admin users",
        Precondition: &mavenagigo.Precondition{
            Group: &mavenagigo.PreconditionGroup{
                Operator: mavenagigo.PreconditionGroupOperatorAnd,
                Preconditions: []*mavenagigo.Precondition{
                    &mavenagigo.Precondition{
                        User: &mavenagigo.MetadataPrecondition{
                            Key: "userKey",
                        },
                    },
                    &mavenagigo.Precondition{
                        User: &mavenagigo.MetadataPrecondition{
                            Key: "userKey2",
                        },
                    },
                },
            },
        },
    }
client.Segments.CreateOrUpdate(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.SegmentRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Segments.Get(SegmentReferenceId) -> *mavenagigo.SegmentResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get a segment by its supplied ID
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.SegmentGetRequest{}
client.Segments.Get(
        context.TODO(),
        "admin-users",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**segmentReferenceId:** `string` — The reference ID of the segment to get. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the segment to get. If not provided, the ID of the calling app will be used.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Segments.Patch(SegmentReferenceId, request) -> *mavenagigo.SegmentResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update mutable segment fields

The `appId` field can be provided to update a segment owned by a different app. 
All other fields will overwrite the existing value on the segment only if provided.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.SegmentPatchRequest{}
client.Segments.Patch(
        context.TODO(),
        "segmentReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**segmentReferenceId:** `string` — The reference ID of the segment to update. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.SegmentPatchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Translations
<details><summary><code>client.Translations.Translate(request) -> *mavenagigo.TranslationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Translate text from one language to another
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.TranslationRequest{
        Text: "Hello world",
        TargetLanguage: "es",
    }
client.Translations.Translate(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.TranslationRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Triggers
<details><summary><code>client.Triggers.Search(request) -> *mavenagigo.EventTriggersSearchResponse</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.EventTriggersSearchRequest{}
client.Triggers.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.EventTriggersSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Triggers.CreateOrUpdate(request) -> *mavenagigo.EventTriggerResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update an event trigger or create it if it doesn't exist.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.EventTriggerRequest{
        TriggerId: &mavenagigo.EntityIdBase{
            ReferenceId: "store-in-snowflake",
        },
        Description: "Stores conversation data in Snowflake",
        Type: mavenagigo.EventTriggerTypeConversationCreated,
    }
client.Triggers.CreateOrUpdate(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.EventTriggerRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Triggers.Get(TriggerReferenceId) -> *mavenagigo.EventTriggerResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an event trigger by its supplied ID
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Triggers.Get(
        context.TODO(),
        "store-in-snowflake",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**triggerReferenceId:** `string` — The reference ID of the event trigger to get. All other entity ID fields are inferred from the request.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Triggers.Delete(TriggerReferenceId) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete an event trigger
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Triggers.Delete(
        context.TODO(),
        "store-in-snowflake",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**triggerReferenceId:** `string` — The reference ID of the event trigger to delete. All other entity ID fields are inferred from the request.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Triggers.PartialUpdate(TriggerReferenceId, request) -> *mavenagigo.EventTriggerResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates an event trigger. Only the enabled field is editable.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.PartialUpdateRequest{
        Body: &mavenagigo.TriggerPartialUpdate{},
    }
client.Triggers.PartialUpdate(
        context.TODO(),
        "triggerReferenceId",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**triggerReferenceId:** `string` — The reference ID of the event trigger to update. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the trigger to update. If not provided, the ID of the calling app will be used.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*mavenagigo.TriggerPartialUpdate` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Users
<details><summary><code>client.Users.Search(request) -> *mavenagigo.AgentUserSearchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Search across all agent users on an agent.

Agent users are a merged view of the users created by individual apps.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.AgentUserSearchRequest{}
client.Users.Search(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.AgentUserSearchRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Users.GetAgentUser(AgentUserId) -> *mavenagigo.AgentUser</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an agent user by its supplied ID.

Agent users are a merged view of the users created by individual apps.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Users.GetAgentUser(
        context.TODO(),
        "aus_1234567890",
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**agentUserId:** `string` — The ID of the agent user to get.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Users.CreateOrUpdate(request) -> *mavenagigo.AppUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update an app user or create it if it doesn't exist.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.AppUserRequest{
        UserId: &mavenagigo.EntityIdBase{
            ReferenceId: "user-0",
        },
        Identifiers: []*mavenagigo.AppUserIdentifier{
            &mavenagigo.AppUserIdentifier{
                Value: "joe@myapp.com",
                Type: mavenagigo.AppUserIdentifyingPropertyTypeEmail,
            },
        },
        Data: map[string]*mavenagigo.UserData{
            "name": &mavenagigo.UserData{
                Value: "Joe",
                Visibility: mavenagigo.VisibilityTypeVisible,
            },
        },
    }
client.Users.CreateOrUpdate(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*mavenagigo.AppUserRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Users.Get(UserId) -> *mavenagigo.AppUserResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get an app user by its supplied ID
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.UserGetRequest{}
client.Users.Get(
        context.TODO(),
        "user-0",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**userId:** `string` — The reference ID of the app user to get. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the app user to get. If not provided the ID of the calling app will be used.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Users.Delete(UserId) -> error</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes all identifiers and user data saved by the specified app.
Does not modify data or identifiers saved by other apps.

If this user is linked to a user from another app, it will not be unlinked. Unlinking of users is not yet supported.

<Warning>This is a destructive operation and cannot be undone.</Warning>
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &mavenagigo.UserDeleteRequest{}
client.Users.Delete(
        context.TODO(),
        "user-0",
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**userId:** `string` — The reference ID of the app user to delete. All other entity ID fields are inferred from the request.
    
</dd>
</dl>

<dl>
<dd>

**appId:** `*string` — The App ID of the app user to delete. If not provided the ID of the calling app will be used.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>
