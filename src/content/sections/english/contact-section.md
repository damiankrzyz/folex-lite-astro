---
enable: true # Control the visibility of this section across all pages where it is used
title: "Ready to Grow Your Business?"
description: "Let's discuss how we can help you achieve your digital marketing goals"

# image: "/images/about-us/about-one.jpg"
# imagePosition: "left" # Choose between "left" or "right"

map:
  enable: false
  position: "right" # Choose between "left" or "right"
  title: "Map of Cheltenham"
  url: https://maps.google.com/maps?width=100%25&amp;height=600&amp;hl=en&amp;q=Cheltenham,+Gloucestershire+(InfiniCore%20Solutions)&amp;t=&amp;z=12&amp;ie=UTF8&amp;iwloc=B&amp;output=embed

# contactInformation:
#   - title: "Headquarters"
#     icon: "/images/icons/svg/location-filled.svg"
#     description: "27 Division St, New York, NY 10002, USA"
#     button:
#       # Refer to the `sharedButton` schema in `src/sections.schema.ts` for all available configuration options (e.g., enable, label, url, hoverEffect, variant, icon, tag, rel, class, target, etc.)
#       enable: true
#       label: "Get Direction"
#       url: "/"
#       # hoverEffect: "" # Optional: text-flip | creative-fill | magnetic | magnetic-text-flip
#       # variant: "" # Optional: fill | outline | text | circle
#       # rel: "" # Optional
#       # target: "" # Optional
#
#   - title: "Email Address"
#     icon: "/images/icons/svg/message-filled.svg"
#     description: |
#       folex.agency@mail.com
#       folex.agency@support.com
#     button:
#       # Refer to the `sharedButton` schema in `src/sections.schema.ts` for all available configuration options (e.g., enable, label, url, hoverEffect, variant, icon, tag, rel, class, target, etc.)
#       enable: true
#       label: "Send Message"
#       url: "mailto:folex.agency@mail.com"
#       # hoverEffect: "" # Optional: text-flip | creative-fill | magnetic | magnetic-text-flip
#       # variant: "" # Optional: fill | outline | text | circle
#       # rel: "" # Optional
#       # target: "" # Optional
#
#   - title: "Phone Number"
#     icon: "/images/icons/svg/phone-filled.svg"
#     description: |
#       +1 800 123 654 987
#       +1 800 223 984 002
#     button:
#       # Refer to the `sharedButton` schema in `src/sections.schema.ts` for all available configuration options (e.g., enable, label, url, hoverEffect, variant, icon, tag, rel, class, target, etc.)
#       enable: true
#       label: "Call Anytime"
#       url: "tel:+1800123654987"
#       # hoverEffect: "" # Optional: text-flip | creative-fill | magnetic | magnetic-text-flip
#       # variant: "" # Optional: fill | outline | text | circle
#       # rel: "" # Optional
#       # target: "" # Optional

# Check config.toml file for form action related settings
# this is also used in the footer of the personal portfolio homepage
form:
  emailSubject: "New inquiry from InfiniCore Solutions website" # Customized email subject (applicable when anyone submit form, form submission may receive by email depend on provider)
  submitButton:
    # Refer to the `sharedButton` schema in `src/sections.schema.ts` for all available configuration options (e.g., enable, label, url, hoverEffect, variant, icon, tag, rel, class, target, etc.)
    enable: true
    label: "SEND MESSAGE"
    # hoverEffect: "" # Optional: text-flip | creative-fill | magnetic | magnetic-text-flip
    # variant: "" # Optional: fill | outline | text | circle
    # rel: "" # Optional
    # target: "" # Optional

  # This note will show at the end of form
  # note: |
  #   Your data is safe with us. We respect your privacy and never share your information. <br /> Read our [Privacy Policy](/privacy-policy/).
  inputs:
    - label: ""
      placeholder: "Full Name *"
      name: "Full Name" # This is crucial. Its indicate under which name you want to receive this field data
      required: true
      halfWidth: true
      defaultValue: ""
    - label: ""
      placeholder: "Email Address *"
      name: "Email Address" # This is crucial. Its indicate under which name you want to receive this field data
      required: true
      type: "email"
      halfWidth: true
      defaultValue: ""
    - label: ""
      placeholder: "Service Interest *"
      name: "Service Interest" # This is crucial. Its indicate under which name you want to receive this field data
      required: true
      halfWidth: false
      dropdown:
        type: "" # select | search - default is select
        search: # if type is search then it will work
          placeholder: ""
        items:
          - label: "Digital Marketing"
            value: "Digital Marketing"
            selected: false
          - label: "SEO Services"
            value: "SEO Services"
            selected: false
          - label: "Social Media Management"
            value: "Social Media Management"
            selected: false
          - label: "Lead Generation"
            value: "Lead Generation"
            selected: false
          - label: "Content Creation"
            value: "Content Creation"
            selected: false
          - label: "Brand Building"
            value: "Brand Building"
            selected: false
          - label: "Product Sourcing"
            value: "Product Sourcing"
            selected: false
          - label: "Business Consulting"
            value: "Business Consulting"
            selected: false
          - label: "General Inquiry"
            value: "General Inquiry"
            selected: true
    - label: ""
      tag: "textarea"
      defaultValue: ""
      rows: "2" # Only work if tag is textarea
      placeholder: "How can we help you *"
      name: "Message" # This is crucial. Its indicate under which name you want to receive this field data
      required: true
      halfWidth: false
    - label: "Google Search" # only valid for type="checkbox" & type === "radio"
      checked: false # only valid for type="checkbox" & type === "radio"
      name: "User Source" # This is crucial. Its indicate under which name you want to receive this field data
      required: true
      groupLabel: "How did you hear about us?" # Radio Inputs Label
      group: "source" # when you add group then it will omit space between the same group radio input
      type: "radio"
      halfWidth: true
      defaultValue: ""
    - label: "Social Media" # only valid for type="checkbox" & type === "radio"
      name: "User Source" # This is crucial. Its indicate under which name you want to receive this field data
      required: true
      groupLabel: "" # Radio Inputs Label
      group: "source" # when you add group then it will omit space between the same group radio input
      type: "radio"
      halfWidth: true
      defaultValue: ""
    # - label: "Referral" # only valid for type="checkbox" & type === "radio"
    #   name: "User Source" # This is crucial. Its indicate under which name you want to receive this field data
    #   required: true
    #   groupLabel: "" # Radio Inputs Label
    #   group: "source" # when you add group then it will omit space between the same group radio input
    #   type: "radio"
    #   halfWidth: true
    #   defaultValue: ""
    # - label: "Other" # only valid for type="checkbox" & type === "radio"
    #   name: "User Source" # This is crucial. Its indicate under which name you want to receive this field data
    #   required: true
    #   groupLabel: "" # Radio Inputs Label
    #   group: "source" # when you add group then it will omit space between the same group radio input
    #   type: "radio"
    #   halfWidth: true
    #   defaultValue: ""
    - label: "I agree to the [terms and conditions](/terms-conditions/) and [privacy policy](/privacy-policy/)." # only valid for type="checkbox" & type === "radio"
      id: "privacy-policy"
      name: "Agreed Privacy" # This is crucial. Its indicate under which name you want to receive this field data
      value: "Agreed" # Value that will be submit (applicable for type="checkbox" & type === "radio")
      checked: false # only valid for type="checkbox" & type === "radio"
      required: true
      type: "checkbox"
      halfWidth: false
      defaultValue: ""
    - note: success # info | warning | success | deprecated | hint
      parentClass: "hidden text-sm message success"
      content: Thank you for contacting InfiniCore Solutions! We'll get back to you as soon as possible.
    - note: deprecated # info | warning | success | deprecated | hint
      parentClass: "hidden text-sm message error"
      content: Something went wrong! Please try again later or check your contact form configuration.
---
