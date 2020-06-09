# User

### Main fields

| Field | Publicly visible | Type | Description |
| :--- | :--- | :--- | :--- |
| \_id | **Yes** | `Integer` | Unique user ID |
| config | No | `Object` | More details in "Config fields" |
| email | No | `String` | Only visible for you |
| email\_MD5 | **Yes** | `String` | MD5 hash of email. Useful for using with Gravatar for example |
| files.used | No | `Integer` | How much space used for files this month |
| files.size | No | `Integer` | Total space for file uploads  |
| files.lastCheckPoint | No | `String` | When space for file uploads is reseted last time |
| fullName | **Yes** | `String` | Full name, max 1000 chars |
| groups | No | `Array<Object>` | More details below in "Groups" |
| password | No | `Boolean` | Does user have a password |
| pro | **Yes** | `Boolean` | PRO subscription |
| proExpire | No | `String` | When PRO subscription will expire |
| registered | No | `String` | Registration date |

### Config fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Publicly visible</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">config.broken_level</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>Broken links finder configuration, possible values:</p>
        <p><code>basic</code>  <code>default</code>  <code>strict</code> or <code>off</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">config.font_color</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Bookmark preview style: <code>sunset</code>  <code>night</code> or empty</td>
    </tr>
    <tr>
      <td style="text-align:left">config.font_size</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Bookmark preview font size: from 0 to 9</td>
    </tr>
    <tr>
      <td style="text-align:left">config.lang</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">UI language in 2 char code</td>
    </tr>
    <tr>
      <td style="text-align:left">config.last_collection</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Last viewed collection ID</td>
    </tr>
    <tr>
      <td style="text-align:left">config.raindrops_sort</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>Default bookmark sort:</p>
        <p><code>title</code>  <code>-title</code>  <code>-sort</code>  <code>domain</code>  <code>-domain</code>  <code>+lastUpdate</code> or <code>-lastUpdate</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">config.raindrops_view</td>
      <td style="text-align:left">No</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>Default bookmark view:</p>
        <p><code>grid</code>  <code>list</code>  <code>simple</code> or <code>masonry</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### Groups object fields <a id="single-group-detail"></a>

| Field | Type | Description |
| :--- | :--- | :--- |
| title | `String` | Name of group |
| hidden | `Boolean` | Does group is collapsed |
| sort | `Integer` | Ascending order position |
| collections | `Array<Integer>` | Collection ID's in order |

### Other fields

| Field | Publicly visible | Type | Description |
| :--- | :--- | :--- | :--- |
| facebook.enabled | No | `Boolean` | Does Facebook account is linked |
| twitter.enabled | No | `Boolean` | Does Twitter account is linked |
| vkontakte.enabled | No | `Boolean` | Does Vkontakte account is linked |
| google.enabled | No | `Boolean` | Does Google account is linked |
| dropbox.enabled | No | `Boolean` | Does Dropbox backup is enabled |
| gdrive.enabled | No | `Boolean` | Does Google Drive backup is enabled |

{% hint style="warning" %}
Our API response could contain **other fields**, not described above. It's **unsafe to use** them in your integration! They could be removed or renamed at any time.
{% endhint %}

