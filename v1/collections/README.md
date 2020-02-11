# Collections

### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">_id</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">The id of the collection.</td>
    </tr>
    <tr>
      <td style="text-align:left">access</td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">access.level</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">
        <p></p>
        <ol>
          <li>read only access (equal to <code>public=true</code>)</li>
          <li>collaborator with read only access</li>
          <li>collaborator with write only access</li>
          <li>owner</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">access.draggable</td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Does it possible to change parent of this collection?</td>
    </tr>
    <tr>
      <td style="text-align:left">collaborators</td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left">When this object is present, means that collections is shared. Content
        of this object is private and not very useful.
        <br />All sharing API methods <a href="sharing.md">described here</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">color</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Primary color of collection cover as <code>HEX</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">count</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Raindrops count</td>
    </tr>
    <tr>
      <td style="text-align:left">cover</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code>
      </td>
      <td style="text-align:left">Collection cover.
        <br />This array always have one item due to legacy reasons</td>
    </tr>
    <tr>
      <td style="text-align:left">created</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">When collection is created</td>
    </tr>
    <tr>
      <td style="text-align:left">expanded</td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Whether the collection&#x2019;s sub-collections are expanded</td>
    </tr>
    <tr>
      <td style="text-align:left">lastUpdate</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">When collection is updated</td>
    </tr>
    <tr>
      <td style="text-align:left">parent</td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">parent.$id</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">The id of the parent collection. Empty for root collection</td>
    </tr>
    <tr>
      <td style="text-align:left">public</td>
      <td style="text-align:left"><code>Boolean</code>
      </td>
      <td style="text-align:left">Collection and raindrops that it contains will be accessible without authentication?</td>
    </tr>
    <tr>
      <td style="text-align:left">sort</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">The order of collection (descending). Defines the position of the collection
        among all the collections with the same <code>parent.$id</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">Name of the collection</td>
    </tr>
    <tr>
      <td style="text-align:left">user</td>
      <td style="text-align:left"><code>Object</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">user.$id</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left">Owner ID</td>
    </tr>
    <tr>
      <td style="text-align:left">view</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">
        <p>View style of collection, can be:</p>
        <ul>
          <li>list (default)</li>
          <li>simple</li>
          <li>grid</li>
          <li>masonry</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>{% hint style="warning" %}
Our API response could contain **other fields**, not described above. It's **unsafe to use** them in your integration! They could be removed or renamed at any time.
{% endhint %}

### System collections

Every user have several system non-removable collections. They are not contained in any API responses.

| \_id | Description |
| :--- | :--- |
| **-1** | "**Unsorted**" collection |
| **-99** | "**Trash**" collection |

