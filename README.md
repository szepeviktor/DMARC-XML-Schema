# Official DMARC XML Schema from RFC-7489

```shell
xmllint --noout --schema XMLSchema.xsd dmarc.xsd
dmarc.xsd validates
```

```shell
xmllint --noout --schema dmarc.xsd example-report.xml
example-report.xml validates
```

## The relaxed schema

```diff
@@ -65,6 +65,9 @@
     <!-- Failure reporting options in effect. -->
     <xs:element name="fo" type="xs:string"
                 minOccurs="0"/>
+    <!-- RFC9091: Requested Mail Receiver policy for non-existent subdomains. -->
+    <xs:element name="np" type="xs:string"
+                minOccurs="0"/>
   </xs:all>
 </xs:complexType>

@@ -143,7 +146,7 @@
                 minOccurs="0"/>
     <!-- The RFC5321.MailFrom domain. -->
     <xs:element name="envelope_from" type="xs:string"
-                minOccurs="1"/>
+                minOccurs="0"/>
     <!-- The RFC5322.From domain. -->
     <xs:element name="header_from" type="xs:string"
                 minOccurs="1"/>
@@ -210,7 +213,7 @@
     <!-- The checked domain. -->
     <xs:element name="domain" type="xs:string" minOccurs="1"/>
     <!-- The scope of the checked domain. -->
-    <xs:element name="scope" type="SPFDomainScope" minOccurs="1"/>
+    <xs:element name="scope" type="SPFDomainScope" minOccurs="0"/>
     <!-- The SPF verification result. -->
     <xs:element name="result" type="SPFResultType"
                 minOccurs="1"/>
@@ -247,7 +250,8 @@
   <xs:complexType>
     <xs:sequence>
       <xs:element name="version"
-                  type="xs:decimal"/>
+                  type="xs:decimal"
+                  minOccurs="0"/>
       <xs:element name="report_metadata"
                   type="ReportMetadataType"/>
       <xs:element name="policy_published"
```
