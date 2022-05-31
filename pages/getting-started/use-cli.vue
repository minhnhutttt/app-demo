<template>
    <ContentWrap>
        <Content>
            <ContentTitle>Using the command line interface</ContentTitle>
            <div class="main">
                <p class="paragraph">The <code>cardano-cli</code> command line interface (CLI) is installed as part
                    of the node
                    installation process. This CLI provides a collection of tools for generating
                    keys, constructing transactions, creating certificates, and other important
                    tasks.</p>
                <p class="paragraph">It is organized in a hierarchy of subcommands, and each level comes with its
                    own
                    built-in documentation of command syntax and options. For more details, read the
                    <a href="https://github.com/input-output-hk/cardano-node/blob/master/doc/reference/cardano-node-cli-reference.md/"
                        target="_blank" rel="noopener noreferrer">CLI command reference</a>.
                </p>
                <p class="paragraph">To access the top level help, type the following command (without arguments):
                </p>
                <p class="paragraph"><code>cardano-cli</code></p>
                <p class="paragraph">All the available sub-subcommands are displayed, one of which is
                    <code>node</code>. To
                    continue drilling down the hierarchy, type the following command:</p>
                <p class="paragraph"><code>cardano-cli node</code></p>
                <p class="paragraph">To learn about the sub-sub-subcommand <code>key-gen</code>, type the following
                    command:</p>
                <p class="paragraph"><code>cardano-cli node key-gen</code></p>
                <p class="paragraph">The parameters that this command takes are displayed. To generate a key-pair of
                    offline keys and a file for the issue counter, type the following command:</p>
                <pre
                    class="css-fkgcw9 ev1gfv90"><pre><pre class="prism-code language-javascript pre" p="3" style="color: rgb(156, 220, 254); background-color: rgb(30, 30, 30);"><div class="token-line"><span class="token plain">   cardano</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">cli node key</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">gen \</span></div><div class="token-line"><span class="token plain">        </span><span class="token operator" style="color: rgb(212, 212, 212);">--</span><span class="token plain">cold</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">verification</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">key</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">file cold</span><span class="token punctuation" style="color: rgb(212, 212, 212);">.</span><span class="token property-access">vkey</span><span class="token plain"> \</span></div><div class="token-line"><span class="token plain">        </span><span class="token operator" style="color: rgb(212, 212, 212);">--</span><span class="token plain">cold</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">signing</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">key</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">file cold</span><span class="token punctuation" style="color: rgb(212, 212, 212);">.</span><span class="token property-access">skey</span><span class="token plain"> \</span></div><div class="token-line"><span class="token plain">        </span><span class="token operator" style="color: rgb(212, 212, 212);">--</span><span class="token plain">operational</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">certificate</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">issue</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">counter</span><span class="token operator" style="color: rgb(212, 212, 212);">-</span><span class="token plain">file cold</span><span class="token punctuation" style="color: rgb(212, 212, 212);">.</span><span class="token property-access">counter</span><span class="token plain"></span></div></pre>
                </pre>
                </pre>
            </div>
            <ContentPosts next-title="Operating a stake pool" next-link="/getting-started/about-stake-pools" prev-title="Installing the Cardano node" prev-link="/getting-started/installing-the-cardano-node/" />
        </Content>
        <ContentAnchor>
        </ContentAnchor>
    </ContentWrap>
</template>