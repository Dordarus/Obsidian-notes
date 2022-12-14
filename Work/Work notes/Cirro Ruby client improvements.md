1. Make mocks for each request, to make testing gem easier
```bash
lib/cirro_io_v2/responses/mock_responses.rb
```

   In that file we will read from test fixtures and return valid mocked object
currently mocking directly from space impossible because of absent attribute problem
still valid for ==version 2.5.0==

## Issue
```ruby
CirroIOV2::Responses::GigResponse.new(
	service.gig_attributes.merge(
		id: 42, object: 'Gig', end_at: 1.year.from_now.to_i
	)
)
```

```ruby
#<struct CirroIOV2::Responses::GigResponse
 id=42,
 object="Gig",
 title="Dignissimos quia.",
 description="Project: PRE-COD Name",
 url="http://localhost:6001/projects/111/tasks/56",
 start_at=1670941067,
 end_at=1702477067,
 archived_at=100,
 total_seats=:auto,
 invitation_mode=
  "{\"$or\":[{\"project_owner_project_ids\":{\"$in\":[111]}},{\"qualifier_project_ids\":{\"$in\":[111]}},{\"admin\":true}]}",
 filter_query=[{:title=>"Qualifying Task", :base_price=>0}],
 tasks={:project_title=>"PRE-COD Name", :task_title=>"Dignissimos quia.", :task_type=>"Qualify"},
 notification_payload=nil,
 epam_options=nil>
```

## Solution
Reinitialise already existed Struct but with `keyword_init: true` option

```ruby
let(:gig_response) do
	gig = Struct.new(
		*CirroIOV2::Responses::GigResponse.members, keyword_init: true
	)
	gig.new(id: 44, end_at: 1.year.from_now.to_i, archived_at: Time.now.to_i)
end
```

### or
Use mocked object directly from Client itself

```ruby
gig = CirroIOV2::MockResponses::GigResponse.new
gig.archived_at = Time.now.to_i
```