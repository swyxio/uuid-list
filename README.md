# uuid-list

list of uuid and hash implementations

## Desirable Properties

- chronologically sortable
- alphabetically sortable?
- 64 bits (instead of 128bits)
- inputs:
  - timestamp
  - 
  
## Concepts

- k-sorting http://ci.nii.ac.jp/naid/110002673489/

    > We’re aiming to keep our k below 1 second, meaning that tweets posted within a second of one another will be within a second of one another in the id space too.

## Impls

- Twitter Snowflake (2010-2014) https://blog.twitter.com/engineering/en_us/a/2010/announcing-snowflake.html
- uuid/v4
